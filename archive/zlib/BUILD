  sedit "s:\${libdir}/pkgconfig:/usr/lib/pkgconfig:" Makefile.in  &&

  export CFLAGS="$CFLAGS -fPIC"  &&

  ./configure  --prefix=/usr  &&
  make                        &&

  ./configure  --prefix=/usr  \
               --libdir=/lib  \
               --shared       &&

  default_make
