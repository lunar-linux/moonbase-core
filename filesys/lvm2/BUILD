(

  CFLAGS+=" -fPIE "
  LDFLAGS+=" -pie "

  if module_installed systemd; then
    OPTS+=" --with-udev_prefix=/usr \
            --with-systemdsystemunitdir=$(pkg-config systemd --variable=systemdsystemunitdir)"
  else
    OPTS+=" --with-udev_prefix=/"
  fi &&


  ./configure  --sbindir=/sbin                \
               --libdir=/lib                  \
               --enable-cmdlib                \
               --enable-pkgconfig             \
               --with-optimisation="$CFLAGS"  \
               --enable-fsadm                 \
               --enable-dmeventd              \
               --enable-applib                \
               --enable-udev_sync             \
               --enable-udev_rules            \
               --enable-static_link           \
               $OPTS                         &&

  default_make

) > $C_FIFO 2>&1
