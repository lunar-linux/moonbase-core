cp -a ../LVM2.$VERSION ../LVM2-initramfs &&

if ! [[ $(arch) == x86_64 ]]; then
  CFLAGS+=" -fPIE " &&
  LDFLAGS+=" -pie "
fi

OPTS+=" --with-udev_prefix=/usr"
if module_installed systemd; then
  OPTS+=" --with-systemdsystemunitdir=/usr/lib/systemd/system"
fi

if module_installed udev || module_installed eudev ; then
   OPTS+=" --enable-udev_sync \
           --enable-udev_rules"
else
  OPTS+=" --enable-udev_sync=no \
          --enable-udev_rules=no \
          --enable-udev-rule-exec-detection=no \
          --enable-udev-systemd-background-jobs=no"
fi

OPTS+=" --libdir=/usr/lib  \
        --enable-fsadm     \
        --enable-cmdlib    \
        --enable-pkgconfig \
        --enable-dmeventd"

default_build &&

# extra udev rule for device-mapper in initramfs
install -D -m644 "${SCRIPT_DIRECTORY}/11-dm-initramfs.rules" /usr/lib/initcpio/udev/ &&

make install_system_dirs &&

cd ../LVM2-initramfs &&

OPTS+=" --enable-udev_sync=no \
      ¦ --enable-udev_rules=no \
      ¦ --enable-udev-systemd-background-jobs=no"

./configure $OPTS &&
cd udev &&
make 69-dm-lvm-metad.rules &&

# extra udev rule for lvmetad in non-systemd initramfs
install -D -m644 69-dm-lvm-metad.rules /usr/lib/dracut/modules.d/90lvm/
