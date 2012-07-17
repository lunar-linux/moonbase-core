(

# fix compiling with glibc 2.16.0
  sed -i '/gets is a security hole/d' lib/stdio.in.h  &&

  bad_flags -malign-double
  default_build

) > $C_FIFO 2>&1
