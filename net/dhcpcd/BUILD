(

  export PREFIX=/usr      &&
  export SYSCONFDIR=/etc  &&
  export CSTD=gnu99       &&

  default_build  &&

  # Now the dhcpcd.service file
  install -Dm 644 {"$SCRIPT_DIRECTORY",/usr/lib/systemd/system}/dhcpcd@.service

) > $C_FIFO 2>&1
