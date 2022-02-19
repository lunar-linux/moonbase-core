CXXFLAGS+=' -std=gnu++98' &&

OPTS+=" --enable-cplusplus --disable-static" &&

default_build &&

# This required header for guile-3.x does not get installed.
install -m 644 include/gc_pthread_redirects.h /usr/include/gc &&

install -m 644 doc/gc.man /usr/share/man/man3
