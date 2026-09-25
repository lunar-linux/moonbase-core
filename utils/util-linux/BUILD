export PYTHONDONTWRITEBYTECODE=1 &&
export DESTDIR=$(pwd)/_pkg &&

#Unknown group 'rfkill', lets make one
add_priv_group rfkill &&

OPTS+=" --enable-agetty     \
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
        --bindir=/usr/bin   \
        --libdir=/usr/lib   \
        --sbindir=/usr/sbin \
        --enable-fs-paths-extra=/usr/bin:/usr/sbin"

default_config &&
make ${MAKES:+-j${MAKES}} &&
mkdir ${DESTDIR} &&
make install DESTDIR=${DESTDIR} &&
chmod 700 ${DESTDIR}/usr/bin/wall &&
chmod 4711 ${DESTDIR}/usr/bin/{newgrp,ch{sh,fn}} &&
ln -sf last ${DESTDIR}/usr/bin/lastb &&
install -g0 -o0 -m755 $SCRIPT_DIRECTORY/make-issue ${DESTDIR}/usr/bin/make-issue &&
install -Dm644 $SCRIPT_DIRECTORY/60-rfkill.rules ${DESTDIR}/usr/lib/udev/rules.d/60-rfkill.rules &&

if module_installed systemd; then
  sedit '/ListenStream/ aRuntimeDirectory=uuidd' ${DESTDIR}/usr/lib/systemd/system/uuidd.socket
fi &&

cd ${DESTDIR} &&
prepare_install &&
cp -arv * / &&

#/usr/lib/tmpfiles.d/uuidd-tmpfiles.conf:6: Failed to resolve user 'uuidd': No such process
add_priv_group uuidd &&
add_priv_user uuidd -d /var/lib/uuidd -g sddm
