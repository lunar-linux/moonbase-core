OPTS+=" -D installed_tests=false \
        -D selinux=disabled"

# Fix SUN-JDK segfault: https://bugzilla.gnome.org/show_bug.cgi?id=755609
LDFLAGS+=" -Wl,-z,nodelete" &&

default_meson_build
