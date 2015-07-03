OPTS+=" --libexecdir=/usr/lib  \
        --enable-split-usr     \
        --enable-compat-libs   \
        --disable-terminal     \
        --disable-audit        \
        --disable-ima          \
        --disable-kdbus        \
        --with-kbd-loadkeys=/usr/bin/loadkeys \
        --with-kbd-setfont=/usr/bin/setfont" &&

add_priv_group systemd-journal &&

# a not existing hostname is set to lunar
if [[ ! -f /etc/hostname ]]; then
   install -m 0644 -o root -g root $SCRIPT_DIRECTORY/files/hostname /etc/hostname
fi &&

# vconsole.conf defaults to us-layout
if [[ ! -f /etc/vconsole.conf ]]; then
   install -m 0644 -o root -g root $SCRIPT_DIRECTORY/files/vconsole.conf /etc/vconsole.conf
fi &&

# last but not least the locale settings, defaulting to US
if [[ ! -f /etc/locale.conf ]]; then
   install -m 0644 -o root -g root $SCRIPT_DIRECTORY/files/locale.conf /etc/locale.conf
fi &&

# systemd guys wrongly assume that on every linux
# installation is a group called "lock" this isn't
# the case in lunar, so we switch it to root.
sedit "s:0775 root lock:0775 root root:" tmpfiles.d/legacy.conf &&

default_config &&
make &&
prepare_install &&

# Needed to migrate from udev module
if module_installed udev; then
  lrm --upgrade udev
fi &&

make install &&

rm -rf /usr/lib/rpm &&

# Disable new naming scheme
if [[ "$NEW_NAME_SCHEME" == "n" && ! -e /etc/udev/rules.d/80-net-setup-link.rules ]]; then
  echo "Disabled the new network interface naming scheme" 
  ln -sf /dev/null /etc/udev/rules.d/80-net-setup-link.rules
fi &&

# Always install the legacy.conf file even if SysV compatibility isn't enabled
install -m 0644 -o root -g root tmpfiles.d/legacy.conf /usr/lib/tmpfiles.d
