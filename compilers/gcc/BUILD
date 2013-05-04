# move libstdc++.so.*-gdb.py to libexec dir
patch_it $SOURCE2 1 &&

# installwatch fails to track files installed using tar
sedit 's;^\(build_install_headers_dir=\).*;\1install-headers-cp;' gcc/config.build &&

# We use libiberty.a from binutils instead
sedit 's/install_to_$(INSTALL_DEST) //' libiberty/Makefile.in  &&

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
             --enable-threads                       \
             --disable-nls                          \
             --enable-target-optspace               \
             --with-gnu-ld                          \
             --with-system-zlib                     \
             --enable-shared                        \
             $OPTS                                 &&

make CFLAGS='-O' LIBCFLAGS='-g -O2' LIBCXXFLAGS='-g -O2 -fno-implicit-templates' bootstrap-lean  &&
prepare_install  &&
make install &&

ln -sf /usr/bin/cpp /usr/lib/gcc/$BUILD/$VERSION/cpp &&
ln -sf /usr/bin/cpp /lib/cpp                         &&
ln -sf gcc          /usr/bin/cc                      &&

# remove the offending broken freetype link
rm -f $MODULE_PREFIX/lib/gcc/$BUILD/$VERSION/include-fixed/freetype
