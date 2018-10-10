# make sure the luser has the source for this one!
WANT_VERSION= download_module wget &&

./config --prefix=/usr         \
         --openssldir=/etc/ssl \
         shared                \
         no-ssl2               \
         no-ssl3               \
         no-ssl3-method        \
         $OPTS                &&

sedit "/^CC/d" Makefile &&
sedit "s/-m486//g" Makefile &&
sedit "s/-O3/-Os/" Makefile &&
sedit "s/^CFLAG=/CFLAG=$CFLAGS /g" Makefile &&

make &&
mkdir _dest &&
make MANDIR=/usr/share/man INSTALL_PREFIX=$(pwd)/_dest install &&
if [ -d _dest/usr/lib64 ]
then
    mv _dest/usr/lib64 _dest/usr/lib
fi &&
prepare_install &&
( cd _dest && cp -r * /) &&
cp $SOURCE_CACHE/$SOURCE2 /etc/ssl/certs/Makefile
