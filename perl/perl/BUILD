OPTS+=" -Dprefix=/usr \
        -Dscriptdir=/usr/bin \
        -Duseshrplib=true \
        -Dman1dir=/usr/share/man/man1 \
        -Dman3dir=/usr/share/man/man3 -d -e" &&

if [ "$CUSTOM" == "y" ] ; then
  ./Configure $OPTS
else
  ./Configure -Dccdlflags='-rdynamic' \
              -Doptimize="${CFLAGS}"  \
              -Duselargefiles \
              -Dusethreads    \
              -Ud_csh         \
              -Dcf_by='Lunar' \
              $OPTS
fi &&

make &&

export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:$SOURCE_DIRECTORY" &&
ldconfig &&

prepare_install &&
make install &&

strip --strip-unneeded $(which perl)
