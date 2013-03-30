(

  # We need to clear the cache dir or otherwise the build is going to fail
  if [ -d /var/cache/fontconfig ] ; then
    rm -f /var/cache/fontconfig/*
  fi

  # There is a documented issue when the user does not have a
  # timezone set (/etc/localtime). It creates invalid XML
  # syntax in a comment located in /etc/fonts/fonts.conf.
  sedit "s:\`date\`::" configure  &&


  ./configure --prefix=/usr     \
              --sysconfdir=/etc \
              --with-templatedir=/etc/fonts/conf.avail \
              --with-xmldir=/etc/fonts \
              --localstatedir=/var     \
              --disable-static         \
              --with-default-fonts=/usr/share/fonts \
              --with-add-fonts=/usr/share/fonts     \
              $OPTS                                &&


#  sedit "s:(BASECONFIGDIR):(CONFIGDIR):" Makefile  &&

  default_make &&

  install -m644 $SCRIPT_DIRECTORY/10-lunar-fonts.conf \
                /etc/fonts/conf.d/

) > $C_FIFO 2>&1
