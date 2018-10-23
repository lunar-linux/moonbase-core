# Do not remove --enable-debug=minimum, it will break some common
# API functions if debug is entirely disabled
OPTS+=" -D installed_tests=false \
        -D fami=false \
        -D selinux=false"

# Fix SUN-JDK segfault: https://bugzilla.gnome.org/show_bug.cgi?id=755609
LDFLAGS+=" -Wl,-z,nodelete" &&

default_meson_build
