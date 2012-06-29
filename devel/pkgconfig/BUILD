(

# a patch for autoconf 2.66
  sedit "s:_PKG_TEXT])dnl:_PKG_TEXT])[]dnl:" pkg.m4  &&

  if ! module_installed pkgconfig
  then

    GLIB_CFLAGS="-I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include" GLIB_LIBS="-lglib-2.0" default_build

  else

    default_build

  fi

) > $C_FIFO 2>&1
