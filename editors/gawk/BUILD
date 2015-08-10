# make a backup for gawk app
cp -f /bin/gawk /bin/gawk.old  &&

OPTS+="--build=$BUILD             \
       --prefix=/usr              \
       --bindir=/bin              \
       --mandir=/usr/share/man    \
       --infodir=/usr/share/info  \
       --without-libsigsegv       \
         ac_cv_func_working_mktime=yes" &&

default_config &&
make &&
prepare_install &&

# restore backup gawk app
mv /bin/gawk.old /bin/gawk &&
ln -sf /bin/gawk /bin/awk  &&

make install &&

ln -sf /bin/gawk /bin/awk &&
rm -f /bin/{,p}gawk-*
