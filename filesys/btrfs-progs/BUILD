(

  sedit 's/^prefix.*/prefix = \//' Makefile
  sedit 's/\/local//' man/Makefile &&
  sedit 's/^bindir.*/bindir = \/sbin/' Makefile &&

  make &&
  prepare_install &&
  make install

) > $C_FIFO 2>&1
