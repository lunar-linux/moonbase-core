# Do not remove --enable-debug=minimum, it will break some common
# API functions if debug is entirely disabled
OPTS+=" -D installed_tests=false \
        -D fami=false \
        -D selinux=disabled"

# Do not install gdbus-codegen, it's part of gdbus-codegen module
sedit '/install.*true/s;true;false;' gio/gdbus-2.0/codegen/meson.build &&

# Fix SUN-JDK segfault: https://bugzilla.gnome.org/show_bug.cgi?id=755609
LDFLAGS+=" -Wl,-z,nodelete" &&

default_meson_build
