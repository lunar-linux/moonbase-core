# make a backup for gawk app
cp -f /usr/bin/gawk /usr/bin/gawk.old  &&

OPTS+=" --libexecdir=/usr/lib" &&

OPTS+=" ac_cv_func_working_mktime=yes" &&

default_build &&

# restore backup gawk app
mv /usr/bin/gawk.old /usr/bin/gawk &&
ln -sf /usr/bin/gawk /usr/bin/awk  &&

make install &&

ln -sf /usr/bin/gawk /usr/bin/awk &&
rm -f /usr/bin/{,p}gawk-*
