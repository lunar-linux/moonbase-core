
OPTS+="--build=$BUILD \
       --prefix=/usr \
       --mandir=/usr/share/man \
       --infodir=/usr/share/info \
       --without-readline \
       ac_cv_func_working_mktime=yes"

# make a backup for gawk app
 if [ -f "/bin/gawk" ]; then
   cp -f /bin/gawk /usr/bin/gawk.old
 else
   cp -f /usr/bin/gawk{,.old}
 fi &&

default_config &&
make &&
prepare_install &&

# restore backup gawk app
mv /usr/bin/gawk{.old,} &&
ln -sf /usr/bin/{g,}awk

make install &&

ln -sf /usr/bin/{g,}awk &&
rm -f /usr/bin/{,p}gawk-* &&

mv /etc/profile.d/gawk.{sh,rc} &&
rm -f /etc/profile.d/gawk.csh
