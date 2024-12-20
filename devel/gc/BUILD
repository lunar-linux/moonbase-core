CXXFLAGS+=' -std=gnu++98' &&

OPTS+=" --enable-cplusplus --disable-static" &&

default_build &&

#Install a missing header requited by guile-3.x
install -m 644 include/gc_pthread_redirects.h /usr/include/gc/
