export CFLAGS="$CFLAGS -fPIC" &&

# binutils needs static the lib
./configure --prefix=/usr &&
make &&

./configure --prefix=/usr \
            --libdir=/lib \
            --shared &&

default_make
