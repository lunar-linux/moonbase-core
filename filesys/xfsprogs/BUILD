export DEBUG=-DNDEBUG &&

# This honors CFLAGS but needs an empty value to avoid 
# default flags.
export OPTIMIZER=" "

OPTS+=" --prefix=/usr --disable-lto" &&

default_config &&
make &&
prepare_install &&

make PKG_ROOT_SBIN_DIR=/usr/sbin PKG_ROOT_LIB_DIR=/usr/lib install install-dev &&

# cleanup static libs
if [ -f "/usr/lib/libhandle.a" ]; then
  rm /usr/lib/libhandle.a
fi
