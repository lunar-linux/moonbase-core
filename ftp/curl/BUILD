echo '/* not used */' > include/curl/types.h &&

if in_depends $MODULE c-ares; then
        OPTS+=" --enable-httpsrr"
fi &&

OPTS+=" --enable-threaded-resolver \
        --enable-versioned-symbols \
        --disable-manual \
        --disable-static \
        --without-libpsl \
        --with-zlib"

default_build &&

install -m644 {,/usr/}include/curl/types.h
