CFLAGS+=" -fPIC"
dstdir=$SOURCE_DIRECTORY/__destdir

mkdir -p build-binutils &&
cd build-binutils &&
mkdir -p $dstdir &&

# Enable 64bit bfd for x86
if [[ "$(uname -m)" == "i686" ]]; then
  OPTS+=" --enable-64-bit-bfd"
fi &&

../configure --prefix=/usr    \
             --sysconfdir=/etc   \
             --disable-gdb    \
             --disable-gdbserver \
             --disable-werror \
             --disable-readline \
             --disable-sim \
             --enable-cet \
             --enable-relro \
             --enable-plugins \
             --enable-threads \
             --enable-ld=default \
             --enable-install-libiberty \
             --enable-shared \
             --with-pic \
             --with-system-zlib \
             $OPTS &&

make configure-host &&
make tooldir=/usr &&
make prefix="$dstdir/usr" tooldir="$dstdir/usr" install &&

# Remove unwanted files
rm $dstdir/usr/share/man/man1/{dlltool,windres,windmc}* &&

# No shared linking to these files outside binutils
rm $dstdir/usr/lib/lib{bfd,opcodes}.so &&
echo "INPUT ( /usr/lib/libbfd.a -liberty -lz -ldl )" > $dstdir/usr/lib/libbfd.so &&
echo "INPUT ( /usr/lib/libopcodes.a -lbfd )" > $dstdir/usr/lib/libopcodes.so

# This part fails on i686, so check the arch
if [[ "$(uname -m)" == "x86_64" || "$(uname -m)" == "aarch64" ]]; then
	mv $dstdir/usr/lib64/* $dstdir/usr/lib/ &&
	rmdir $dstdir/usr/lib64
fi &&

prepare_install &&

cp -rf --remove-destination $dstdir/* /
