if ! in_depends $MODULE db; then
  sedit 's/arpd//' misc/Makefile
fi &&

default_build &&

install -Dm644 include/libnetlink.h /usr/include/libnetlink.h &&
install -Dm644 lib/libnetlink.a /usr/lib/libnetlink.a
