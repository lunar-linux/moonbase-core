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
        --disable-last      \
        --disable-reset     \
        --disable-static    \
        --disable-wall      \
        --enable-libmount-force-mountinfo" &&

default_build &&
chmod 4711 /usr/bin/{newgrp,ch{sh,fn}} &&
install -g0 -o0 -m755 $SCRIPT_DIRECTORY/make-issue /usr/bin/make-issue &&

sedit '/ListenStream/ aRuntimeDirectory=uuidd' /usr/lib/systemd/system/uuidd.socket
