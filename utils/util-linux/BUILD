OPTS+=" --enable-agetty     \
        --enable-chfn-chsh  \
        --enable-fsck       \
        --enable-mesg       \
        --enable-partx      \
        --enable-raw        \
        --enable-rename     \
        --enable-schedutils \
        --enable-vipw       \
        --enable-write      \
        --disable-kill      \
        --disable-last      \
        --disable-reset     \
        --disable-static    \
        --disable-sulogin   \
        --disable-wall      \
        --enable-libmount-force-mountinfo \
        --enable-fs-paths-extra=/usr/bin" &&

# --enable-newgrp
# --with-python=3

default_build &&

install -g0 -o0 -m755 $SCRIPT_DIRECTORY/make-issue /usr/bin/make-issue &&

sedit '/ListenStream/ aRuntimeDirectory=uuidd' /usr/lib/systemd/system/uuidd.socket
