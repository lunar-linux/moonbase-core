if ! in_depends $MODULE db; then
  sedit 's/arpd//' misc/Makefile
fi &&

./configure &&

make &&

prepare_install &&

make SBINDIR=/usr/sbin install &&

install -Dm644 include/libnetlink.h /usr/include/libnetlink.h &&
install -Dm644 lib/libnetlink.a /usr/lib/libnetlink.a
