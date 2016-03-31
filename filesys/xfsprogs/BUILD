export DEBUG=-DNDEBUG &&

OPTS+=" --prefix=/usr \
        --sbindir=/usr/sbin" &&

DEST_DIR=$SOURCE_DIRECTORY/xfs_build
mkdir -p $DEST_DIR &&

default_config &&
make &&
make DESTDIR=$DEST_DIR PKG_ROOT_SBIN_DIR="/usr/sbin" install install-dev &&
mv -f $DEST_DIR/lib*/* $DEST_DIR/usr/lib/
rm -rf $DEST_DIR/lib

# cleanup static libs
if [ -f "$DEST_DIR/usr/lib/libhandle.a" ]; then
  rm $DEST_DIR/usr/lib/libhandle.a
fi

if [ -f "$DEST_DIR/usr/lib/libhandle.la" ]; then
  rm $DEST_DIR/usr/lib/libhandle.la
fi

prepare_install &&

cp -fr $DEST_DIR/usr/* /usr/
