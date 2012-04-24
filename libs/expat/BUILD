(

  OPTS+=" --disable-static" &&

  sedit "s/\/man\/man1/\/share\/man\/man1/g" Makefile.in &&

  default_build &&

  # Let's be naughty and do the coverup
  ln -sf /usr/lib/libexpat.so /usr/lib/libexpat.so.0

) > $C_FIFO 2>&1
