# using -pipe causes spurious test-suite failures
CFLAGS=${CFLAGS/-pipe/} &&
CXXFLAGS=${CXXFLAGS/-pipe/} &&

mkdir BUILD &&
cd BUILD &&

LANGUAGES="${LANGUAGES:=c++}" &&

../configure --build=$BUILD                         \
             --host=$BUILD                          \
             --prefix=${MODULE_PREFIX}              \
             --libdir=${MODULE_PREFIX}/lib          \
             --libexecdir=${MODULE_PREFIX}/lib      \
             --infodir=${MODULE_PREFIX}/share/info  \
             --mandir=${MODULE_PREFIX}/share/man    \
             --enable-languages=$LANGUAGES          \
             --enable-__cxa_atexit                  \
             --enable-threads=posix                 \
             --enable-target-optspace               \
             --enable-shared                        \
             --enable-libmpx                        \
             --with-lto                             \
             --with-gnu-ld                          \
             --with-system-zlib                     \
             --disable-nls                          \
             --disable-werror                       \
             --disable-libssp                       \
             --disable-multilib                     \
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
ln -sf /usr/bin/gcc /usr/bin/cc &&

# POSIX conformance launcher scripts for c89 and c99
cat > /usr/bin/c89 <<"EOF"
#!/bin/sh
fl="-std=c89"
for opt; do
  case "$opt" in
    -ansi|-std=c89|-std=iso9899:1990) fl="";;
    -std=*) echo "`basename $0` called with non ANSI/ISO C option $opt" >&2
        exit 1;;
  esac
done
exec gcc $fl ${1+"$@"}
EOF

cat > /usr/bin/c99 <<"EOF"
#!/bin/sh
fl="-std=c99"
for opt; do
  case "$opt" in
    -std=c99|-std=iso9899:1999) fl="";;
    -std=*) echo "`basename $0` called with non ISO C99 option $opt" >&2
        exit 1;;
  esac
done
exec gcc $fl ${1+"$@"}
EOF

chmod 755 /usr/bin/c{8,9}9 &&

# remove the offending broken freetype link
rm -f $MODULE_PREFIX/lib/gcc/$BUILD/$VERSION/include-fixed/freetype
