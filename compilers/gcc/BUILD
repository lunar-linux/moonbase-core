# using -pipe causes spurious test-suite failures
bad_flags -pipe &&

mkdir BUILD &&
cd BUILD &&

LANGUAGES="${LANGUAGES:=c++}" &&

../configure --build=$BUILD                         \
             --host=$BUILD                          \
             --prefix=${MODULE_PREFIX}              \
             --libdir=${MODULE_PREFIX}/lib          \
             --libexecdir=${MODULE_PREFIX}/libexec  \
             --infodir=${MODULE_PREFIX}/share/info  \
             --mandir=${MODULE_PREFIX}/share/man    \
             --enable-languages=$LANGUAGES          \
             --enable-__cxa_atexit                  \
             --enable-libmpx                        \
             --enable-threads=posix                 \
             --disable-nls                          \
             --enable-target-optspace               \
             --with-lto                             \
             --with-gnu-ld                          \
             --with-system-zlib                     \
             --enable-shared                        \
             --disable-multilib                     \
             --disable-werror                       \
             --disable-libssp                       \
             --disable-libstdcxx-pch                \
             --disable-libunwind-exceptions         \
             $OPTS                                 &&

make CFLAGS='-O' LIBCFLAGS='-g -O2' LIBCXXFLAGS='-g -O2 -fno-implicit-templates' bootstrap-lean &&
prepare_install &&
make install &&

install -d /usr/share/gdb/auto-load &&
mv /usr/lib/libstdc++.so.6.*-gdb.py /usr/share/gdb/auto-load/ &&

ln -sf /usr/bin/cpp /usr/lib/gcc/$BUILD/$VERSION/cpp &&
ln -sf /usr/bin/cpp /lib/cpp &&
ln -sf gcc          /usr/bin/cc &&

# POSIX conformance launcher scripts for c89 and c99
install -m0755 {${SCRIPT_DIRECTORY},/usr/bin}/c89 &&
install -m0755 {${SCRIPT_DIRECTORY},/usr/bin}/c99 &&

# remove the offending broken freetype link
rm -f $MODULE_PREFIX/lib/gcc/$BUILD/$VERSION/include-fixed/freetype
