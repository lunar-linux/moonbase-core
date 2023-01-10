export PYTHONDONTWRITEBYTECODE=1 &&

OPTS+=" -Drootprefix=/usr \
        -Daudit=false \
        -Dgnu-efi=true \
        -Dima=false \
        -Dlibidn2=true \
        -Dsplit-usr=true \
        -Dfallback-hostname=lunarlinux \
        -Drpmmacrosdir=no \
        -Dsysvinit-path= \
        -Dsysvrcnd-path= \
        -Dsbat-distro=lunarlinux \
        -Dsbat-distro-summary=lunarlinux \
        -Dsbat-distro-url=https://www.lunar-linux.org/
        -Dhomed=false"

add_priv_group systemd-journal &&

if in_depends $MODULE docbook-xsl; then
 export XML_CATALOG_FILES=/etc/xml/catalog
fi &&

# a not existing hostname is set to lunar.
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

default_meson_config &&
ninja -C build/ &&
prepare_install &&

# Needed to migrate from udev module
if module_installed udev; then
  lrm --upgrade udev
fi &&

ninja -C build/ install &&

# Disable new naming scheme
if [[ "$NEW_NAME_SCHEME" == "n" && ! -e /etc/udev/rules.d/80-net-setup-link.rules ]]; then
  echo "Disabled the new network interface naming scheme"
  ln -sf /dev/null /etc/udev/rules.d/80-net-setup-link.rules
fi
