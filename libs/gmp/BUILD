OPTS="--enable-cxx --enable-fat --disable-static" &&

default_config &&
make &&
make check &&
prepare_install &&
make install &&

ln -sf /usr/lib/libgmp.so /usr/lib/libgmp.so.3
