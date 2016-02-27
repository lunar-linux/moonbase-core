tar xf ${MODULE}_${VERSION}_src.tar &&
cd ${MODULE}_${VERSION}_src &&

yes | ./Configure linux &&
make &&

prepare_install &&

install -Dm0755 lsof /usr/bin/lsof &&
install -Dm0644 lsof.8 /usr/share/man/man8/lsof.8
