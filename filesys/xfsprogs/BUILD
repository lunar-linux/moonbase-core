export DEBUG=-DNDEBUG &&

OPTS+=" --prefix=/usr \
        --sbindir=/usr/bin" &&

default_config &&
make &&
prepare_install &&

make PKG_ROOT_SBIN_DIR="/usr/sbin" install install-dev &&

# this might be required by userland tools
ln -sf /lib/libhandle.so.1 /usr/lib/libhandle.so.1

# cleanup static libs
if [ -f "/usr/lib/libhandle.a" ]; then
  rm /usr/lib/libhandle.a
fi

#if [ -f "/usr/lib/libhandle.la" ]; then
#  rm /usr/lib/libhandle.la
#fi
