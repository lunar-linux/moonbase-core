(

  sedit 's:(localstatedir)/locatedb:(localstatedir)/cache/locate/locatedb:g' locate/Makefile.in  &&
  sedit 's:PRUNEPATHS="/tmp :PRUNEPATHS="/proc /tmp :g' locate/updatedb.sh  &&

  # Fixes an incompatibility with glibc 2.16
  sedit '/gets is a/d' gnulib/lib/stdio.in.h &&

  default_build               &&
  mkdir -p /var/cache/locate  &&
  if [ -f /var/cache/locatedb ] ; then
    mv /var/cache/locatedb /var/cache/locate
  fi

) > $C_FIFO 2>&1
