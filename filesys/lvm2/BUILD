if ! [[ $(arch) == x86_64 ]]; then
  CFLAGS+=" -fPIE " &&
  LDFLAGS+=" -pie "
fi

if module_installed systemd; then
  OPTS+=" --with-udev_prefix=/usr \
          --with-systemdsystemunitdir=$(pkg-config systemd --variable=systemdsystemunitdir)"
else
  OPTS+=" --with-udev_prefix=/"
fi &&

OPTS+=" --libdir=/usr/lib  \
        --enable-cmdlib    \
        --enable-pkgconfig \
        --enable-fsadm     \
        --enable-dmeventd  \
        --enable-applib    \
        --enable-udev_sync \
        --enable-udev_rules"

default_build &&

make install_system_dirs
