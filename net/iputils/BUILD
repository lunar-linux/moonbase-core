make &&

prepare_install &&

install -m755 arping clockdiff rdisc tracepath tracepath6 traceroute6 rarpd tftpd /usr/bin/ &&

install -m4711 ping /usr/bin/ &&
ln -sf /usr/bin/ping /usr/bin/ping6 &&

if [ "`get_module_config DOCS`" = "y" ] && [ module_installed docbook-utils ]; then
  # generate manpages and html documentation
  make man &&
  make html
else
  # manpages are manually created and packed by lunar devs
  cd $BUILD_DIRECTORY &&
  unpack $SOURCE2 --strip-components=1 &&
  cd $SOURCE_DIRECTORY
fi &&

install -dm755 /usr/share/man/man8 &&
install -m644 doc/{clockdiff,arping,rdisc,tracepath,traceroute6,rarpd,ping,tftpd}.8 /usr/share/man/man8/ &&

ln -sf ping.8.gz /usr/share/man/man8/ping6.8.gz &&
ln -sf tracepath.8.gz /usr/share/man/man8/tracepath6.8.gz &&

gather_docs doc/*.html

