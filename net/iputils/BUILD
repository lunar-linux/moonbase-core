make USE_NETTLE=no USE_GNUTLS=no &&

prepare_install &&

install -m755 arping clockdiff rdisc tracepath traceroute6 rarpd tftpd /usr/bin/ &&

install -m4711 ping /usr/bin/ &&
ln -sf /usr/bin/ping /usr/bin/ping6 &&

if in_depends $MODULE docbook-utils; then
  # generate manpages and html documentation
  make man
#  make html
else
  # manpages are manually created and packed by lunar devs
  cd $BUILD_DIRECTORY &&
  unpack $SOURCE2 --strip-components=1 &&
  cd $SOURCE_DIRECTORY
fi &&

install -dm755 /usr/share/man/man8 &&
install -m644 doc/{clockdiff,arping,rdisc,tracepath,traceroute6,rarpd,ping,tftpd}.8 /usr/share/man/man8/ &&

ln -sf ping.8.gz /usr/share/man/man8/ping6.8.gz &&

if in_depends $MODULE docbook-utils; then
  gather_docs doc/*.html
fi
