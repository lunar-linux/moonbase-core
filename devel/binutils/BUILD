# Following the build procedure used by the LFS folks
mkdir -p build-binutils &&
cd build-binutils &&

CFLAGS+=" -fPIC"

../configure --prefix=/usr    \
             --disable-gdb    \
             --disable-werror \
             --enable-shared  \
             --enable-threads \
             --enable-gold    \
             --enable-plugins \
             --enable-install-libiberty \
             --with-system-zlib \
             $OPTS &&

make configure-host &&
make tooldir=/usr &&

prepare_install &&

make tooldir=/usr install &&

#make tooldir=/usr install-info &&
#mkdir -p $DOCUMENT_DIRECTORY/binutils &&
#cp -p ../binutils/NEWS ../binutils/ChangeLog $DOCUMENT_DIRECTORY/binutils &&

# For some reason installwatch fail to pick up the ld hardlink, touching it solves that issue
if [ -e /usr/bin/ld ]; then
  touch /usr/bin/ld
fi &&

# Remove unwanted files
# nlmconv
rm /usr/share/man/man1/{dlltool,windres,windmc}*

# No shared linking to these files outside binutils
rm /usr/lib/lib{bfd,opcodes}.so &&
echo "INPUT ( /usr/lib/libbfd.a -liberty -lz -ldl )" > /usr/lib/libbfd.so &&
echo "INPUT ( /usr/lib/libopcodes.a -lbfd )" > /usr/lib/libopcodes.so
