(

  patch_it $SOURCE2 1 &&
  patch_it $SOURCE3 1 &&

  if ! in_depends $MODULE db; then
    sedit 's/arpd//' misc/Makefile
  fi &&

  ./configure &&
  KERNEL_INCLUDE=/usr/include/ make &&
  prepare_install &&
  make install

) > $C_FIFO 2>&1
