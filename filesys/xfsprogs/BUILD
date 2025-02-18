export DEBUG=-DNDEBUG &&

# This honors CFLAGS but needs an empty value to avoid 
# default flags.
export OPTIMIZER=" "

OPTS+=" --prefix=/usr --enable-lib64=no --disable-static --disable-lto" &&

default_config &&
make config &&

# fix the build for the new icu4c version
sed -r -i 's/\$\(LIBICU_LIBS\)/\0 -licuuc/' scrub/Makefile

make &&
prepare_install &&

make PKG_ROOT_SBIN_DIR=/usr/sbin PKG_ROOT_LIB_DIR=/usr/lib install install-dev
