(

  sedit 's:/usr/local:$(DESTDIR)/usr:g;s:/usr/share/man:$(DESTDIR)/usr/share/man:g;s:/usr/etc:/etc:g' Makefile config.c &&
  sedit "s:-O2:$CFLAGS:" Makefile &&
  mkdir -p ${DESTDIR}/{etc,usr/bin,usr/share/man/man8}
  default_make

) > $C_FIFO 2>&1
