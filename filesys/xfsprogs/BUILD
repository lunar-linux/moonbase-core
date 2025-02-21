export DEBUG=-DNDEBUG &&

# /usr/bin/ld: /usr/lib64/libicuuc.so.76: error adding symbols: DSO missing from command line
if module_installed icu4c ; then
sed -r -i 's/\$\(LIBICU_LIBS\)/\0 -licuuc/' scrub/Makefile
fi &&

# This honors CFLAGS but needs an empty value to avoid 
# default flags.
export OPTIMIZER=" "

OPTS+=" --prefix=/usr --enable-lib64=no --disable-static --disable-lto" &&

default_build

make PKG_ROOT_SBIN_DIR=/usr/sbin PKG_ROOT_LIB_DIR=/usr/lib install install-dev
