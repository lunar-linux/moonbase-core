if ! [[ $(arch) == x86_64 ]]; then
  CFLAGS+=" -fPIE " &&
  LDFLAGS+=" -pie "
  sedit 's/CLDFLAGS.*-Wl,-z,relro/& -shared/' libdm/make.tmpl.in
  sedit 's/CLDFLAGS.*-Wl,-z,relro/& -shared/' make.tmpl.in
fi

if module_installed systemd; then
  OPTS+=" --with-udev_prefix=/usr \
          --with-systemdsystemunitdir=$(pkg-config systemd --variable=systemdsystemunitdir)"
else
  OPTS+=" --with-udev_prefix=/ \
          --with-systemdsystemunitdir=no"
fi &&

OPTS+=" --libdir=/usr/lib  \
        --enable-fsadm     \
        --enable-cmdlib    \
        --enable-dmeventd  \
        --enable-pkgconfig \
        --enable-udev_sync \
        --enable-udev_rules"

default_build &&

make install_system_dirs
