# Fix linking libmagic (vfork needs libpthread)
CFLAGS+=" -pthread"

# seccomp breaks file -z foo.xz
# does a whole pipe-fork-exec dance with /bin/xz, so difficult to fix

OPTS+=" --datadir=/usr/share/file \
        --enable-fsect-man5 \
        --disable-static \
        --disable-libseccomp"

default_build
