# inotify now has a auto switch so if CONFIG_INOTIFY_USER is set it will
# be enabled and likewise disabled if the not present in the kernel
OPTS+=" -Dqt_help=disabled             \
        -Druntime_dir=/run             \
        -Dmodular_tests=disabled       \
        -Ddbus_user=messagebus         \
        -Drelocation=disabled          \
        -Dmodular_tests=disabled       \
        -Duser_session=true            \
        -Dsystem_pid_file=/run/dbus/dbus.pid \
        -Dsystem_socket=/run/dbus/system_bus_socket \
        -Dlaunchd=disabled        \
        -Dx11_autolaunch=disabled \
        -Dducktype_docs=disabled  \
        -Dxml_docs=disabled       \
        -Ddoxygen_docs=disabled"

if module_installed systemd; then
  OPTS+=" -Dsystemd_system_unitdir=/usr/lib/systemd/system"
fi &&

default_meson_build
