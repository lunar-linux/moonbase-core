# Its include conflicts with glibc:/usr/include/crypt.h and
# its /usr/lib/libcrypt.so conflicts with glibc
OPTS+=" --enable-hashes=strong,glibc \
        --enable-obsolete-api=no \
        --disable-failure-tokens \
        --disable-static \
        --disable-werror \
        --libdir=/usr/lib \
        --includedir=/usr/include \
        " &&

default_build
