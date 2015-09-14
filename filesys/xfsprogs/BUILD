export DEBUG=-DNDEBUG

OPTS+=" --prefix=/usr \
        --sbindir=/usr/bin" &&

default_config &&
make &&
prepare_install &&

make PKG_ROOT_SBIN_DIR="/usr/sbin" install install-dev
