if [ "$CUSTOM" == "y" ] ; then
  ./Configure  -Dprefix=/usr \
               -Dscriptdir=/usr/bin \
               -Duseshrplib=true \
               $OPTS \
               -Dman1dir=/usr/share/man/man1 \
               -Dman3dir=/usr/share/man/man3 -e
else
  ./Configure  -Dprefix=/usr \
               -Dscriptdir=/usr/bin \
               -Duseshrplib=true       \
               -Dccdlflags='-rdynamic' \
               -Doptimize="${CFLAGS}"  \
               -Duselargefiles \
               -Ud_csh         \
               -Dcf_by='Lunar' \
               $OPTS \
               -Dman1dir=/usr/share/man/man1 \
               -Dusethreads  \
               -Dman3dir=/usr/share/man/man3 -d -e
fi &&

make &&

export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:$SOURCE_DIRECTORY" &&
ldconfig &&

prepare_install &&
make install &&

strip --strip-unneeded $(which perl)
