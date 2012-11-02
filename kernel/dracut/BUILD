(

  patch_it $SOURCE2 1 &&

  prepare_install &&
  make prefix=/usr sysconfdir=/etc install &&

  # Removing modules we don't support
  rm -rf /usr/lib/dracut/modules.d/{01fips,02fips-aesni,95fcoe,80cms,95dasd,95dasd_mod,95zfcp,95znet} &&

  # We always install this file (which means overwriting)
  install -m 0644 -g root -o root $SCRIPT_DIRECTORY/files/01-lunar.conf /etc/dracut.conf.d/ &&

  gather_docs HACKING TODO AUTHORS

) > $C_FIFO 2>&1
