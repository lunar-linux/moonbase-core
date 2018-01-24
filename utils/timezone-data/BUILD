# preserve the existing /etc/localtime symlink
if [ -f /etc/localtime ]; then
  mv -f /etc/localtime /etc/localtime.tmp.bak
fi &&

default_make &&

# restore the original /etc/localtime file
if [ -f /etc/localtime.tmp.bak ]; then
  mv -f /etc/localtime.tmp.bak /etc/localtime
fi
