if [ "$ENABLE_LARGEFILE" == "y" ]; then
  CFLAGS+=" \$(BIGFILES)"
fi &&

# build shared lib first so the app part will
# not complain about the missing static lib
make -f Makefile-libbz2_so PREFIX=/usr &&
# HACK - bzip2 seems to depend on bzip2 already being installed
ln -s libbz2.so.1.0 libbz2.so &&
make PREFIX=/usr LD_LIBRARY_PATH=${LD_LIBRARY_PATH:.} &&

prepare_install &&
make PREFIX=/usr install &&

# shared libs have to be installed separately
install -m755 libbz2.so.1.0.6 /usr/lib/libbz2.so.1.0.6 &&
ln -sf /usr/lib/libbz2.so.1.0.6 /usr/lib/libbz2.so.1.0 &&
ln -sf /usr/lib/libbz2.so.1.0 /usr/lib/libbz2.so.1 &&
ln -sf /usr/lib/libbz2.so.1 /usr/lib/libbz2.so &&

strip /usr/bin/bzip2 /usr/bin/bzip2recover /usr/bin/bzcat /usr/bin/bunzip2
