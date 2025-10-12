OPTS="--enable-cxx --enable-fat --disable-static"
LIBTOOL=/usr/bin/libtool

autoconf &&
default_config &&
make LIBTOOL=$LIBTOOL &&
make check LIBTOOL=$LIBTOOL &&
prepare_install &&
make install LIBTOOL=$LIBTOOL &&

ln -sf /usr/lib/libgmp.so /usr/lib/libgmp.so.3
