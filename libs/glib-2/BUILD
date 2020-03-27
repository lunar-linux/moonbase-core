OPTS+=" -D installed_tests=false \
        -D fam=false \
        -D selinux=disabled"

# Do not install gdbus-codegen, it's part of gdbus-codegen module
sedit '/install_dir/d' gio/gdbus-2.0/codegen/meson.build &&

# Fix SUN-JDK segfault: https://bugzilla.gnome.org/show_bug.cgi?id=755609
LDFLAGS+=" -Wl,-z,nodelete" &&

default_meson_build
