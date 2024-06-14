
./configure --prefix=/usr \
            --bindir=/usr/bin \
            --mandir=/usr/share/man \
            --infodir=/usr/share/info \
            CPPFLAGS="$CPPFLAGS" \
            CFLAGS="$CFLAGS" \
            LDFLAGS="$LDFLAGS" &&

default_make &&

prepare_install &&
make install &&

# red.1 was pointing to ed.1 but only ed.1.gz exists
rm /usr/share/man/man1/red.1 &&
ln -sv ed.1.gz /usr/share/man/man1/red.1.gz
