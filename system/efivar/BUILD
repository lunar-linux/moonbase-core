CFLAGS="${CFLAGS} -flto"

OPTS+=" libdir=/usr/lib/ \
        bindir=/usr/bin/ \
        mandir=/usr/share/man/ \
        includedir=/usr/include/ -j1" &&

default_make &&

# build and install efivar-tester
cd src/test &&
make $OPTS &&
install -D -m0755 $SOURCE_DIRECTORY/src/test/tester /usr/bin/efivar-tester
