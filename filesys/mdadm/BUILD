# Does not automatically pick up $CFLAGS
make CXFLAGS="$CFLAGS" UDEVDIR=/usr/lib/udev BINDIR=/usr/sbin &&

prepare_install &&

make BINDIR=/usr/sbin install &&

# Some non-usr-merged systems considerations
if [[ ! -L /bin ]]; then
  ln -sfv /usr/sbin/mdadm /bin/ &&
  ln -sfv /usr/sbin/mdmon /bin/
fi
