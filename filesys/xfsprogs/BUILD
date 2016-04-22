export DEBUG=-DNDEBUG &&

OPTS+=" --prefix=/usr \
        --sbindir=/usr/bin" &&

DEST_DIR=$SOURCE_DIRECTORY/xfs_build
mkdir -p $DEST_DIR/usr/lib &&

default_config &&
make &&
#make DESTDIR=$DEST_DIR PKG_ROOT_SBIN_DIR="/usr/bin" install install-dev &&
make PKG_ROOT_LIB_DIR=$DEST_DIR PKG_ROOT_SBIN_DIR=$DEST_DIR/usr/bin install install-dev &&
cp -fr $DEST_DIR/lib* $DEST_DIR/usr/lib/
rm -rf $DEST_DIR/lib*

# cleanup static libs
if [ -f "$DEST_DIR/usr/lib/libhandle.a" ]; then
  rm $DEST_DIR/usr/lib/libhandle.a
fi

if [ -f "$DEST_DIR/usr/lib/libhandle.la" ]; then
  rm $DEST_DIR/usr/lib/libhandle.la
fi

prepare_install &&

cp -fr $DEST_DIR/usr/* /usr/
