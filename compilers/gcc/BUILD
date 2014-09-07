
#sedit 's/trap 0/trap "" 0/' configure  &&

mkdir BUILD  &&
cd BUILD     &&

LANGUAGES="${LANGUAGES:=c++}"  &&

../configure --build=$BUILD                         \
             --host=$BUILD                          \
             --enable-languages=$LANGUAGES          \
             --prefix=${MODULE_PREFIX}              \
             --infodir=${MODULE_PREFIX}/share/info  \
             --mandir=${MODULE_PREFIX}/share/man    \
             --enable-__cxa_atexit                  \
             --enable-threads=posix                 \
             --disable-nls                          \
             --enable-target-optspace               \
             --with-gnu-ld                          \
             --with-system-zlib                     \
             --enable-shared                        \
             --disable-multilib                     \
             --disable-werror                       \
             $OPTS                                 &&

make CFLAGS='-O' LIBCFLAGS='-g -O2' LIBCXXFLAGS='-g -O2 -fno-implicit-templates' bootstrap-lean  &&
prepare_install  &&
make install &&

ln -sf /usr/bin/cpp /usr/lib/gcc/$BUILD/$VERSION/cpp &&
ln -sf /usr/bin/cpp /lib/cpp                         &&
ln -sf gcc          /usr/bin/cc                      &&

# remove the offending broken freetype link
rm -f $MODULE_PREFIX/lib/gcc/$BUILD/$VERSION/include-fixed/freetype
