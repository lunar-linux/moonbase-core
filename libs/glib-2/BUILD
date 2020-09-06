# Do not remove --enable-debug=minimum, it will break some common
# API functions if debug is entirely disabled
OPTS+=" -D fam=false \
        -D selinux=disabled \
        -D installed_tests=false"

# Fix SUN-JDK segfault: https://bugzilla.gnome.org/show_bug.cgi?id=755609
LDFLAGS+=" -Wl,-z,nodelete"

# Do not install gdbus-codegen, it's part of gdbus-codegen module
sedit '/install_dir/d' gio/gdbus-2.0/codegen/meson.build &&
default_meson_build
