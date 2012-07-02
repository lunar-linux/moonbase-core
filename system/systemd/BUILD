(

  OPTS+=" --with-distro=other \
          --libexecdir=/usr/lib \
          --with-usb-ids-path=/usr/share/usb.ids \
          --with-pci-ids-path=/usr/share/pci.ids \
          --enable-split-usr \
          --disable-tcpwrap"

  # gtk is broken currently
  OPTS+=" --disable-gtk"

  # just adding some files which are useful to
  # systemd
  # todo: some info-message to the user, that
  #       he/she should adjust /etc/hostname,
  #       /etc/vconsole.conf and /etc/locale.conf
  #       could be useful.

  # a not existing hostname is set to lunar.
  [ ! -f /etc/hostname ] && install -m 0644 -o root -g root $SCRIPT_DIRECTORY/files/hostname /etc/hostname

  # vconsole.conf defaults to us-layout
  [ ! -f /etc/vconsole.conf ] && install -m 0644 -o root -g root $SCRIPT_DIRECTORY/files/vconsole.conf /etc/vconsole.conf

  # os-release should properly show lunar
  # todo: we might replace this with some auto-generated
  #       values from /etc/lunar.release in the future.
  [ ! -f /etc/os-release ] && install -m 0644 -o root -g root $SCRIPT_DIRECTORY/files/os-release /etc/os-release

  # last but not least the locale settings, defaulting to US
  [ ! -f /etc/locale.conf ] && install -m 0644 -o root -g root $SCRIPT_DIRECTORY/files/locale.conf /etc/locale.conf

  patch_it $SOURCE2 1 &&
  patch_it $SOURCE3 1 &&
  patch_it $SOURCE4 1 &&

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

  make install

) > $C_FIFO 2>&1
