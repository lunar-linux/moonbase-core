OPTS="--enable-cxx --enable-fat --disable-static"

default_config &&
sed -i -e 's/ -shared / -Wl,-O1,--as-needed\0/g' libtool &&
make &&
make check &&
prepare_install &&
make install &&

ln -sf /usr/lib/libgmp.so /usr/lib/libgmp.so.3
