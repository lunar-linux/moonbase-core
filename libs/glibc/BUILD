export CC=gcc
CFLAGS+=" -O2 "

bad_flags "-Wp,-D_FORTIFY_SOURCE=2" "-fno-plt" &&

if [ -n "$MAKES" ] && [ "$MAKES" -gt 1 ]; then
  sedit "s/# PARALLELMFLAGS = -j 4/PARALLELMFLAGS = -j $MAKES/" Makefile.in
fi &&

# Don't fully strip libc
if [[ "$LDFLAGS" == *-s* ]]; then
  STRIP=y
fi &&

mkdir -p $SOURCE_DIRECTORY/glibc-build &&
cd $SOURCE_DIRECTORY/glibc-build &&

echo "slibdir=/usr/lib" >> configparms &&
echo "rtlddir=/lib" >> configparms &&
echo "sbindir=/usr/bin" >> configparms &&

../configure --prefix=/usr             \
             --infodir=/usr/share/info \
             --mandir=/usr/share/man   \
             --host=$BUILD   \
             --build=$BUILD  \
             --with-headers=/usr/include \
             --with-bugurl=https://github.com/lunar-linux/moonbase-core/issues \
             --enable-cet          \
             --enable-shared       \
             --enable-kernel=4.4   \
             --enable-add-ons      \
             --enable-bind-now     \
             --enable-lock-elision \
             --enable-stack-protector=strong \
             --enable-stackguard-randomization \
             --disable-systemtap      \
             --disable-werror         \
             --disable-profile        \
             --disable-multi-arch     \
             --disable-timezone-tools \
             $OPTS &&

# build libraries with hardening disabled
echo "build-programs=no" >> configparms &&
make -O &&

# Re-enable hardening
sedit '/build-programs=/s;no;yes;'   configparms &&
echo "CFLAGS += -Wp,-D_FORTIFY_SOURCE=2" >> configparms
make -O &&
make info &&

_GLIBC_ROOT="$SOURCE_DIRECTORY/__glibcdest" &&

mkdir -p $_GLIBC_ROOT/{lib,usr/lib} &&

if [ "$(arch)" == "x86_64" ]; then
  ln -s lib $_GLIBC_ROOT/lib64 &&
  ln -s lib $_GLIBC_ROOT/usr/lib64
else
  ln -s lib $_GLIBC_ROOT/lib32 &&
  ln -s lib $_GLIBC_ROOT/usr/lib32
fi &&

make install_root="$_GLIBC_ROOT" install &&

# Generate locale info
if [ -z "$GLIBC_LOCALES" ]; then
  make install_root="$_GLIBC_ROOT" localedata/install-locales
else
  for LOCALE in $GLIBC_LOCALES; do
    INPUTFILE=$(echo $LOCALE | cut -d/ -f1 | sed -e 's:\..*$::g') &&
    OUTPUTFILE=$(echo $LOCALE | cut -d/ -f1) &&
    CHARMAP=$(echo  $LOCALE | cut -d/ -f2)   &&
    mkdir -p $_GLIBC_ROOT/usr/lib/locale/$OUTPUTFILE     &&
    echo "localedef -i $INPUTFILE -f $CHARMAP $OUTPUTFILE" &&
    localedef --prefix=$_GLIBC_ROOT -i $INPUTFILE -f $CHARMAP $OUTPUTFILE
  done
fi &&

# Now optionally perform safe stripping of binaries and libs
if [[ "$STRIP" == "y" ]]; then
  find "$_GLIBC_ROOT"/usr/bin -type f -executable -exec strip $STRIP_BINARIES {} + 2> /dev/null || true &&
  find "$_GLIBC_ROOT"/usr/lib -name '*.a' -type f -exec strip $STRIP_STATIC {} + 2> /dev/null || true &&
  find "$_GLIBC_ROOT"/usr/lib "$_GLIBC_ROOT"/lib \
       -not -name 'ld-*.so*' \
       -not -name 'libc.so*' \
       -not -name 'libpthread.so*' \
       -not -name 'libthread_db.so*' \
       -name '*.so' -type f -exec strip $STRIP_SHARED {} + 2> /dev/null || true
fi &&

prepare_install &&

cp -rf --remove-destination $_GLIBC_ROOT/* / &&

# Rebuild the ld cache
rm -f /etc/ld.so.cache 2>/dev/null &&
ldconfig &&

if [ ! -e /etc/nscd.conf ]; then
  install -m644 $SOURCE_DIRECTORY/nscd/nscd.conf /etc/nscd.conf
fi &&

if [ ! -e /etc/gai.conf ]; then
  install -m644 $SOURCE_DIRECTORY/posix/gai.conf /etc/gai.conf
fi
