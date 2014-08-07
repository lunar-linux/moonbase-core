  # setting the ssl option
  if in_depends $MODULE openssl && module_installed "openssl" ; then
        OPTS+=" --with-ssl=openssl"
  elif in_depends $MODULE gnutls && module_installed "gnutls" ; then
        OPTS+=" --with-ssl"
  else
        OPTS+=" --without-ssl"
  fi &&

  ./configure --build=$BUILD             \
              --prefix=/usr              \
              --bindir=/usr/bin          \
              --sbindir=/usr/sbin        \
              --datadir=/usr/share       \
              --sysconfdir=/etc          \
              --localstatedir=/var       \
              --libdir=/usr/lib          \
              --includedir=/usr/include  \
              --infodir=/usr/share/info  \
              --mandir=/usr/share/man    \
              --disable-debug            \
              $OPTS                     &&

   default_make
