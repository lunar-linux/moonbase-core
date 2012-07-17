(

# fix compiling with glibc 2.16.0
  sed -i '/gets is a security hole/d' gnulib/lib//stdio.in.h  &&

  sedit 's:(localstatedir)/locatedb:(localstatedir)/cache/locate/locatedb:g' locate/Makefile.in  &&
  sedit 's:PRUNEPATHS="/tmp :PRUNEPATHS="/proc /tmp :g' locate/updatedb.sh  &&

  default_build               &&
  mkdir -p /var/cache/locate  &&
  if [ -f /var/cache/locatedb ] ; then
    mv /var/cache/locatedb /var/cache/locate
  fi

) > $C_FIFO 2>&1
