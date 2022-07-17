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
        --enable-systemd               \
        --with-dbus-user=messagebus    \
        --with-console-auth-dir=/run/console/ \
        --with-system-pid-file=/run/dbus/dbus.pid \
        --with-system-socket=/run/dbus/system_bus_socket \
        --with-systemdsystemunitdir=/usr/lib/systemd/system \
        --without-x"

default_build

#install -Dm755 $SCRIPT_DIRECTORY/30-dbus /etc/X11/xinit/xinitrc.d/30-dbus
