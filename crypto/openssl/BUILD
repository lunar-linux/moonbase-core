# make sure the luser has the source for this one!
WANT_VERSION= download_module wget &&

./config --prefix=/usr         \
         --openssldir=/etc/ssl \
         shared                \
         no-ssl3               \
         no-ssl3-method        \
         $OPTS                &&

sedit "/^CC/d" Makefile &&
sedit "s/-m486//g" Makefile &&
sedit "s/-O3/-Os/" Makefile &&
sedit "s/^CFLAG=/CFLAG=$CFLAGS /g" Makefile &&

make &&
prepare_install &&
make MANDIR=/usr/share/man install &&
cp $SOURCE_CACHE/$SOURCE2 /etc/ssl/certs/Makefile
