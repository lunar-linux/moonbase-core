if [ "$ENABLE_LARGEFILE" == "y" ]; then
  CFLAGS+=" \$(BIGFILES)"
fi &&

# build shared lib first so the app part will
# not complain about the missing static lib
make -f Makefile-libbz2_so PREFIX=/usr &&
# HACK - bzip2 seems to depend on bzip2 already being installed
ln -s libbz2.so.1.0 libbz2.so &&
make PREFIX=/usr LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:. &&
make PREFIX=/usr LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:. libbz2.a &&

prepare_install &&
make -f $SCRIPT_DIRECTORY/Makefile.destdir PREFIX=/usr install &&

# shared libs have to be installed separately
install -m755 libbz2.so.1.0.6 ${DESTDIR:-}/usr/lib/libbz2.so.1.0.6 &&
ln -sf libbz2.so.1.0.6 ${DESTDIR:-}/usr/lib/libbz2.so.1.0 &&
ln -sf libbz2.so.1.0 ${DESTDIR:-}/usr/lib/libbz2.so.1 &&
ln -sf libbz2.so.1 ${DESTDIR:-}/usr/lib/libbz2.so &&

strip ${DESTDIR:-}/usr/bin/bzip2 ${DESTDIR:-}/usr/bin/bzip2recover ${DESTDIR:-}/usr/bin/bzcat ${DESTDIR:-}/usr/bin/bunzip2
