OPTS+=" --enable-agetty      \
        --disable-kill       \
        --disable-su         \
        --disable-nologin    \
        --disable-last       \
        --disable-mesg       \
        --enable-partx       \
        --enable-raw         \
        --enable-rename      \
        --disable-reset      \
        --disable-login      \
        --disable-static     \
        --disable-sulogin    \
        --enable-schedutils  \
        --disable-wall       \
        --enable-write       \
        --enable-fsck"      &&

default_build &&

install -g0 -o0 -m755 $SCRIPT_DIRECTORY/make-issue /usr/sbin/make-issue
