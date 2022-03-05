CXXFLAGS+=' -std=gnu++98' &&

OPTS+=" --enable-cplusplus --disable-static" &&

default_build &&

install -m 644 doc/gc.man /usr/share/man/man3 &&

#Install a missing header requited by guile-3.x
install -m 644 include/gc_pthread_redirects.h /usr/include/gc/
