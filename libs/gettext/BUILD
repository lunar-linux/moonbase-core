  # Fixes an incompatibility with glibc-2.16
  sedit '/gets is a/d' gettext-*/*/stdio.in.h &&

  if !( module_installed emacs ); then
      OPTS+=" --without-emacs"
  fi  &&

  ./configure  --build=$BUILD             \
               --host=$BUILD              \
               --prefix=/usr              \
               --sysconfdir=/etc          \
               --mandir=/usr/share/man    \
               --infodir=/usr/share/info  \
               --disable-csharp           \
               --without-libintl-prefix   \
               --disable-static           \
               $OPTS                     &&
  default_make
