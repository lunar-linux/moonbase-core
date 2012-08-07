(

  bad_flags -malign-double

  # Fixes an incompatibility with glibc-2.16
  sedit '/gets is a/d' lib/stdio.in.h &&

  default_build

) > $C_FIFO 2>&1
