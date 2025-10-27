OPTS+=" --with-udev_prefix=/usr \
        --with-systemdsystemunitdir=$(pkg-config systemd --variable=systemdsystemunitdir)"

OPTS+=" --libdir=/usr/lib  \
        --enable-fsadm     \
        --enable-cmdlib    \
        --enable-dmeventd  \
        --enable-pkgconfig \
        --enable-udev_sync \
        --enable-udev_rules"

default_build &&

make install_system_dirs
