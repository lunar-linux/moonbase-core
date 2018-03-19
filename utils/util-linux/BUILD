OPTS+=" --enable-agetty     \
        --enable-chfn-chsh  \
        --enable-fsck       \
        --enable-mesg       \
        --enable-partx      \
        --enable-raw        \
        --enable-rename     \
        --enable-schedutils \
        --enable-vipw       \
        --enable-newgrp     \
        --enable-write      \
        --disable-kill      \
        --disable-reset     \
        --disable-static    \
        --enable-fs-paths-extra=/usr/bin" &&


default_config &&
make ${MAKES:+-j${MAKES}} &&
mkdir _pkg &&
make install DESTDIR=$(cd _pkg && pwd) &&
mv _pkg/sbin/sulogin _pkg/usr/sbin &&
chmod 700 _pkg/usr/bin/wall &&
chmod 4711 _pkg/usr/bin/{newgrp,ch{sh,fn}} &&
if module_installed systemd; then
  sedit '/ListenStream/ aRuntimeDirectory=uuidd' _pkg/usr/lib/systemd/system/uuidd.socket
fi &&
cd _pkg &&

prepare_install &&

find . -depth -print0 | cpio -0pdmuv / &&

# allow only the root user to use wall command
install -g0 -o0 -m755 $SCRIPT_DIRECTORY/make-issue /usr/bin/make-issue
