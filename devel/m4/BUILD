(
  # Fixes an incompatibility with glibc-2.16
  sedit '/gets is a/d' lib/stdio.in.h &&

  sedit "s/\infodir = \$(prefix)\/info/infodir = \$(prefix)\/share\/info/" Makefile.in  &&
  ./configure  --build=$BUILD  \
               --prefix=/usr   \
               $OPTS          &&

  sedit "s/fix)\/info/fix)\/share\/info/" Makefile  &&

  default_make

) > $C_FIFO 2>&1
