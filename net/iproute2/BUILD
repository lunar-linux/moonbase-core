if ! in_depends $MODULE db; then
  sedit 's/arpd//' misc/Makefile
fi &&

./configure &&

make &&

prepare_install &&

# this is need for ip static function
make SBINDIR=/usr/bin install &&

install -Dm644 include/libnetlink.h /usr/include/libnetlink.h &&
install -Dm644 lib/libnetlink.a /usr/lib/libnetlink.a
