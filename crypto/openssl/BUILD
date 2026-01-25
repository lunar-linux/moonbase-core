# make sure the luser has the source for this one!
WANT_VERSION= download_module wget &&

# mark stack as non-executable
./config --prefix=/usr \
         --openssldir=/etc/ssl \
         shared \
         no-brotli \
         no-brotli-dynamic \
         no-ssl3 \
         no-ssl3-method \
         $(arch | grep -q x86_64 && echo enable-ec_nistp_64_gcc_128) \
         $([[ "$DOCS" == "n" ]] && echo no-docs) \
         "-Wa,--noexecstack" \
         $OPTS

sedit "/^CC/d" Makefile &&
sedit "s/-O3/-Os/" Makefile &&

make LIBDIR=lib &&
prepare_install &&
make LIBDIR=lib MANDIR=/usr/share/man install &&
cp $SOURCE_CACHE/$SOURCE2 /etc/ssl/certs/Makefile
