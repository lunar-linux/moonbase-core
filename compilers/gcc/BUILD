# using -pipe causes spurious test-suite failures
bad_flags -pipe &&

mkdir BUILD &&
cd BUILD &&

LANGUAGES="${LANGUAGES:=c++}" &&

OPTS+=" --build=$BUILD                \
        --host=$BUILD                 \
        --prefix=/usr                 \
        --libdir=/usr/lib             \
        --infodir=/usr/share/info     \
        --mandir=/usr/share/man       \
        --enable-languages=$LANGUAGES \
        --enable-gnu-unique-object    \
        --enable-ckecking=release     \
        --enable-target-optspace      \
        --enable-linker-build-id      \
        --enable-threads=posix        \
        --enable-__cxa_atexit         \
        --enable-clocale=gnu          \
        --enable-shared               \
        --enable-libmpx               \
        --enable-plugin               \
        --enable-lto                  \
        --with-gnu-ld                 \
        --with-system-zlib            \
        --disable-nls                 \
        --disable-werror              \
        --disable-libssp              \
        --disable-multilib            \
        --disable-libstdcxx-pch       \
        --disable-libunwind-exceptions" &&

OPTS+=" --libexecdir=/usr/lib" &&

../configure $OPTS &&

make CFLAGS='-O' LIBCFLAGS='-g -O2' LIBCXXFLAGS='-g -O2 -fno-implicit-templates' bootstrap-lean &&
prepare_install &&
make install &&

( cd /usr/lib/gcc/`arch`-pc-linux-gnu/$VERSION &&
  strip cc1 cc1plus lto1 ) &&

install -d /usr/share/gdb/auto-load &&
mv /usr/lib/libstdc++.so.6.*-gdb.py /usr/share/gdb/auto-load/ &&

ln -sf /usr/bin/cpp /usr/lib/gcc/$BUILD/$VERSION/cpp &&
ln -sf gcc /usr/bin/cc &&

# POSIX conformance launcher scripts for c89 and c99
install -m0755 {${SCRIPT_DIRECTORY},/usr/bin}/c89 &&
install -m0755 {${SCRIPT_DIRECTORY},/usr/bin}/c99 &&

# remove the offending broken freetype link
rm -f /usr/lib/gcc/$BUILD/$VERSION/include-fixed/freetype &&

ln -sf /usr/bin/cpp /lib/cpp
