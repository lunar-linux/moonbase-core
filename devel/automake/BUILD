(

  default_build &&

  #the lines below arfe for the "automake" and "aclocal" symlinks, needed by some sources
  rm -Rf /usr/share/automake &&
  ln -sf /usr/share/automake-${VERSION::4} /usr/share/automake

) > $C_FIFO 2>&1
