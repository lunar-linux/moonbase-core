make &&

prepare_install &&

make destdir=/usr \
     sbindir=/usr/bin \
     mandir=/usr/share/man \
     install &&

install -D -m 0755 wiper/wiper.sh /usr/bin/wiper.sh &&
install -D -m 0644 wiper/README.txt /usr/share/doc/wiper/README.txt
