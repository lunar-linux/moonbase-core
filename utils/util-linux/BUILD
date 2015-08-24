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

# for systems with /bin a symlink of /usr/bin
# OPTS+=" --bindir=/usr/bin --libdir=/usr/lib --sbindir=/usr/sbin" &&

default_build &&

install -g0 -o0 -m755 $SCRIPT_DIRECTORY/make-issue /usr/sbin/make-issue
