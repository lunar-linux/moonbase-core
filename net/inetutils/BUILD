(

  # To prevent compilation error:  undefined reference to `tgetent'
  export LIBS+=" -lncurses" &&

  OPTS+=" --disable-servers   \
          --disable-ifconfig  \
          --disable-tftp      \
          --disable-logger    \
          --disable-ftp       \
          --disable-whois     \
          --disable-rpath"   &&

  # Fixes an incompatibility with glibc-2.16
  sedit '/gets is a/d' lib/stdio.in.h &&

  default_build

) > $C_FIFO 2>&1
