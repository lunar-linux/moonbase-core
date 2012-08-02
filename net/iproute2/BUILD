(

  sedit "s:/usr/lib/:lib/:" Makefile &&
  sedit "s:\$(DESTDIR)\$(CONFDIR):\$(CONFDIR):" Makefile &&
  sedit "s:\$(DESTDIR)\$(ARPDDIR):\$(ARPDDIR):" Makefile &&

  if ! in_depends $MODULE db; then
    sedit 's/arpd//' misc/Makefile
  fi &&

  chmod +x configure &&
  ./configure &&
  KERNEL_INCLUDE=/usr/include/ make SBINDIR=/usr/sbin &&
  prepare_install &&
  make SBINDIR=/usr/sbin install

) > $C_FIFO 2>&1
