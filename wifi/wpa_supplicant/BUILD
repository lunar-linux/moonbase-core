cd wpa_supplicant &&
cp $SCRIPT_DIRECTORY/config ./.config &&

if ! in_depends $MODULE dbus; then
  sedit '/CONFIG_CTRL_IFACE_DBUS.*=/s;y;n;g' .config
fi &&

make LIBDIR=/usr/lib BINDIR=/usr/bin &&
prepare_install  &&
make LIBDIR=/usr/lib BINDIR=/usr/bin install &&

install -d -m755 /etc/wpa_supplicant &&
# Don't overwrite existing config
[ -e /etc/wpa_supplicant/wpa_supplicant.conf ] ||
  install -m644 wpa_supplicant.conf /etc/wpa_supplicant/wpa_supplicant.conf &&

if module_installed systemd; then
  install -d -m755 /etc/dbus-1/system.d/ &&
  install -d -m755 /usr/lib/systemd/system/ &&
  install -m644 dbus/dbus-wpa_supplicant.conf /etc/dbus-1/system.d/wpa_supplicant.conf &&
  install -m644 systemd/*.service /usr/lib/systemd/system/ &&
  install -m644 dbus/fi.w1.wpa_supplicant1.service /usr/share/dbus-1/system-services/
fi &&

gather_docs developer.txt wpa_supplicant.conf

