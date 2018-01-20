OPTS+=" --disable-static\
        --enable-shared \
        --enable-thread-safe" &&

if [ -f /usr/lib/libmpfr.so.4.1.6 ]; then
# preserve the old version to prevent the crash of gcc
  cp /usr/lib/libmpfr.so.4.1.6 /usr/lib/libmpfr.so.4.1.6.old
fi &&

if [ -f /usr/lib/libmpfr.so.1.2.2 ]; then
# preserve the old version to prevent the crash of gcc
  cp /usr/lib/libmpfr.so.1.2.2 /usr/lib/libmpfr.so.1.2.2.old
fi &&

default_build &&

if [ -f /usr/lib/libmpfr.so.4.1.6.old ]; then
# restore the old version to prevent the crash of gcc
  mv -f /usr/lib/libmpfr.so.4.1.6.old /usr/lib/libmpfr.so.4.1.6 &&
  ln -sf /usr/lib/libmpfr.so.4.1.6 /usr/lib/libmpfr.so.4
fi &&

if [ -f /usr/lib/libmpfr.so.1.2.2.old ]; then
# restore the old version to prevent the crash of gcc
  mv -f /usr/lib/libmpfr.so.1.2.2.old /usr/lib/libmpfr.so.1.2.2 &&
  ln -sf /usr/lib/libmpfr.so.1.2.2 /usr/lib/libmpfr.so.1
fi
