export PYTHONDONTWRITEBYTECODE=1 &&

#Unknown group 'rfkill', lets make one
add_priv_group rfkill &&

OPTS+=" --bindir=/usr/bin   \
        --sbindir=/usr/sbin \
        --libdir=/usr/lib   \
        --enable-agetty     \
        --enable-chfn-chsh  \
        --enable-fsck       \
        --enable-mesg       \
        --enable-partx      \
        --enable-rename     \
        --enable-schedutils \
        --enable-vipw       \
        --enable-newgrp     \
        --enable-write      \
        --disable-kill      \
        --disable-static    \
        --enable-fs-paths-extra=/usr/bin:/usr/sbin"

default_config &&
make ${MAKES:+-j${MAKES}} &&
mkdir _pkg &&
make install DESTDIR=$(cd _pkg && pwd) &&
chmod 700 _pkg/usr/bin/wall &&
chmod 4711 _pkg/usr/bin/{newgrp,ch{sh,fn}} &&
if module_installed systemd; then
  sedit '/ListenStream/ aRuntimeDirectory=uuidd' _pkg/usr/lib/systemd/system/uuidd.socket
fi &&

cd _pkg &&
prepare_install &&
find . -depth -print0 | cpio -0pdmuv / &&

# Some non usr-merged considerations, as well as the next block of code
if [[ -d /bin ]]; then
  ln -sv ../usr/bin/mount /bin/
  ln -sv ../usr/bin/umount /bin/
fi &&

if [[ -d /sbin ]]; then
  ln -sv ../usr/sbin/swapon /sbin/
  ln -sv ../usr/sbin/swapoff /sbin/
  ln -sv ../usr/sbin/agetty /sbin/
fi &&

install -g0 -o0 -m755 $SCRIPT_DIRECTORY/make-issue /usr/bin/make-issue &&
install -Dm644 $SCRIPT_DIRECTORY/60-rfkill.rules /usr/lib/udev/rules.d/60-rfkill.rules &&
ln -sf /usr/bin/last /usr/bin/lastb &&

#/usr/lib/tmpfiles.d/uuidd-tmpfiles.conf:6: Failed to resolve user 'uuidd': No such process
add_priv_group uuidd &&
add_priv_user uuidd -d /var/lib/uuidd -g sddm
