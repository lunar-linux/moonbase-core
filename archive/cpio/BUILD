(

  # Fixes an incompatibility with glibc-2.16
  sedit '/gets is a/d' gnu/stdio.in.h &&
  default_config  &&
  if module_installed mt-st ; then
    sedit 's/install:: installdirs all/install:: installdirs/' Makefile  &&
    make cpio rmt
  else
    make
  fi               &&
  prepare_install  &&
  make install
  
) > $C_FIFO 2>&1
