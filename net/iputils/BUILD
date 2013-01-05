(

  # manpages is manually created and packed by lunar devs
  tar xvf $SOURCE_CACHE/$SOURCE2 --strip-components=1 &&
  
  # Set $CFLAGS
  sedit "s;^CCOPTOPT=;CCOPTOPT=$CFLAGS ;" Makefile &&
  cat Makefile &&

  make  &&
  prepare_install  &&

  install -dm755 /usr/{sbin,bin} &&
  install -m755 clockdiff arping rdisc tracepath tracepath6 traceroute6 rarpd tftpd /usr/sbin/ &&
  install -m4711 ping ping6 /usr/bin/ &&
  install -dm755 /usr/share/man/man8 &&
  install -m644 doc/{clockdiff,arping,rdisc,tracepath,traceroute6,rarpd,ping,tftpd}.8 /usr/share/man/man8/ &&

  ln -sf ping.8.gz /usr/share/man/man8/ping6.8.gz &&
  ln -sf tracepath.8.gz /usr/share/man/man8/tracepath6.8.gz &&

  gather_docs doc/*.html

) > $C_FIFO 2>&1
