if kernel_option_present CONFIG_INOTIFY_USER; then
  OPTS+=" --enable-inotify"
else
  OPTS+=" --disable-inotify"
fi &&

OPTS+=" --localstatedir=/var           \
        --libexecdir=/usr/lib/dbus-1.0 \
        --disable-static               \
        --disable-tests                \
        --disable-asserts              \
        --disable-verbose-mode         \
        --enable-user-session          \
        --with-dbus-user=messagebus    \
        --with-session-socket-dir=/tmp \
        --with-console-auth-dir=/run/console/ \
        --with-system-pid-file=/var/run/dbus/dbus.pid \
        --with-system-socket=/run/dbus/system_bus_socket" &&

if module_installed systemd; then
  OPTS+=" --with-systemdsystemunitdir=/usr/lib/systemd/system --enable-systemd"
fi &&

default_build &&

# The following used to be in POST_INSTALL but the service wasn't starting
# on FIRST install due to the lack of existing /var/lib/dbus
add_priv_user messagebus:messagebus -d /dev/null -s /bin/false &&
mkdir -p /var/run/dbus &&
chown -R messagebus:messagebus /var/run/dbus &&

mkdir -p /etc/X11/xinit/xinitrc.d/ &&
install -m755 $SCRIPT_DIRECTORY/30-dbus /etc/X11/xinit/xinitrc.d/
