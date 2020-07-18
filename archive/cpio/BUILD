CFLAGS+=' -fcommon' # fix the compilation with gcc 10.x

OPTS+=" --exec-prefix=/usr \
        --mandir=/usr/share/man"

default_build &&

# remove the rmt application
rm -f /usr/bin/rmt &&
rm -f /usr/share/man/man8/rmt.8 &&

# remove infodir
rm /usr/share/info/dir
