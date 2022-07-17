if kernel_option_present CONFIG_INOTIFY_USER; then
  OPTS+=" --enable-inotify"
else
  OPTS+=" --disable-inotify"
fi

OPTS+=" --localstatedir=/var           \
        --libexecdir=/usr/lib/dbus-1.0 \
        --runstatedir=/run             \
        --disable-static               \
        --disable-tests                \
        --disable-asserts              \
        --disable-verbose-mode         \
        --enable-user-session          \
        --with-dbus-user=messagebus    \
        --with-console-auth-dir=/run/console/ \
        --with-system-pid-file=/run/dbus/dbus.pid \
        --with-system-socket=/run/dbus/system_bus_socket \
        --without-x"

if module_installed systemd; then
  OPTS+=" --with-systemdsystemunitdir=/usr/lib/systemd/system --enable-systemd"
fi &&


default_build
