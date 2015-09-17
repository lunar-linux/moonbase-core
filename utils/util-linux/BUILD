OPTS+=" --enable-agetty     \
        --enable-chfn-chsh  \
        --enable-fsck       \
        --enable-partx      \
        --enable-raw        \
        --enable-rename     \
        --enable-schedutils \
        --enable-vipw       \
        --enable-write      \
        --disable-kill      \
        --disable-last      \
        --disable-mesg      \
        --disable-reset     \
        --disable-static    \
        --disable-sulogin   \
        --disable-wall"    &&

default_build &&

install -g0 -o0 -m755 $SCRIPT_DIRECTORY/make-issue /usr/bin/make-issue
