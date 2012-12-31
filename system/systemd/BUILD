(

  OPTS+=" --libexecdir=/usr/lib \
          --enable-split-usr \
          --disable-tcpwrap"

  # a not existing hostname is set to lunar.
  [ -f /etc/hostname ] || install -m 0644 -o root -g root $SCRIPT_DIRECTORY/files/hostname /etc/hostname &&

  # vconsole.conf defaults to us-layout
  [ -f /etc/vconsole.conf ] || install -m 0644 -o root -g root $SCRIPT_DIRECTORY/files/vconsole.conf /etc/vconsole.conf &&

  # last but not least the locale settings, defaulting to US
  [ -f /etc/locale.conf ] || install -m 0644 -o root -g root $SCRIPT_DIRECTORY/files/locale.conf /etc/locale.conf &&

  # systemd guys wrongly assume that on every linux
  # installation is a group called "lock" this isn't
  # the case in lunar, so we switch it to root.
  sedit "s:0775 root lock:0775 root root:" tmpfiles.d/legacy.conf &&

  patch_it $SOURCE2 1 &&
  autoreconf &&

  default_config &&
  make &&
  prepare_install &&

  # Needed to migrate from udev module
  if module_installed udev; then
    lrm --upgrade udev
  fi &&

  # systemd is no longer PSAFE during the make install phase due to install order of some libs (systemd-journal).
  # Please check if this is fixed with the next release.
  unset MAKES &&
  make install &&

  # Always install the legacy.conf file even if SysV compatibility isn't enabled
  install -m 0644 -o root -g root tmpfiles.d/legacy.conf /usr/lib/tmpfiles.d

) > $C_FIFO 2>&1
