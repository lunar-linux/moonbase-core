# make sure the luser has the source for this one!
WANT_VERSION= download_module wget &&

# mark stack as non-executable
./config --prefix=/usr \
         --openssldir=/etc/ssl \
         shared \
         no-ssl3 \
         no-ssl3-method \
         $(arch | grep -q x86_64 && echo enable-ec_nistp_64_gcc_128) \
         "-Wa,--noexecstack" \
         $OPTS

sedit "/^CC/d" Makefile &&
sedit "s/-O3/-Os/" Makefile &&

make &&
prepare_install &&
make MANDIR=/usr/share/man install &&
cp $SOURCE_CACHE/$SOURCE2 /etc/ssl/certs/Makefile
