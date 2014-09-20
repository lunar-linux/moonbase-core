if kernel_option_present CONFIG_INOTIFY_USER ; then
  OPTS+=" --enable-inotify"
else
  OPTS+=" --disable-inotify"
fi

OPTS+=" --disable-static               \
        --localstatedir=/var           \
        --with-session-socket-dir=/tmp \
        --with-dbus-user=messagebus    \
        --disable-xml-docs             \
        --with-init-scripts=none       \
        --disable-verbose-mode         \
        --disable-tests                \
        --disable-asserts              \
        --with-system-pid-file=/var/run/messagebus.pid"

if module_installed systemd; then
  OPTS+=" --with-systemdsystemunitdir=/usr/lib/systemd/system \
          --enable-systemd"
fi

default_build  &&

# The following used to be in POST_INSTALL but the service wasn't starting
# on FIRST install due to the lack of existing /var/lib/dbus
add_priv_user messagebus:messagebus -d /dev/null -s /bin/false  &&
mkdir -p /var/run/dbus  &&
chown -R messagebus:messagebus /var/run/dbus  &&

mkdir -p /etc/X11/xinit/xinitrc.d/  &&
install -m755 $SCRIPT_DIRECTORY/30-dbus /etc/X11/xinit/xinitrc.d/
