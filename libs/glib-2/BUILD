# Do not remove --enable-debug=minimum, it will break some common
# API functions if debug is entirely disabled
export OPTS+=" --enable-debug=minimum \
               --disable-static \
               --enable-shared \
               --disable-fam" &&

# Fix SUN-JDK segfault: https://bugzilla.gnome.org/show_bug.cgi?id=755609
LDFLAGS+=" -Wl,-z,nodelete" &&

AT_M4DIR=. autoreconf &&

default_build
