export DEBUG=-DNDEBUG &&
sed -r -i 's/\$\(LIBICU_LIBS\)/\0 -licuuc/' scrub/Makefile &&
# This honors CFLAGS but needs an empty value to avoid 
# default flags.
export OPTIMIZER=" "

OPTS+=" --prefix=/usr --enable-lib64=no --disable-static --disable-lto" &&

default_config &&
make &&
prepare_install &&

make PKG_ROOT_SBIN_DIR=/usr/sbin PKG_ROOT_LIB_DIR=/usr/lib install install-dev
