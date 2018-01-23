# preserve the existing /etc/localtime symlink
[ -f /etc/localtime ] && mv -f /etc/localtime /etc/localtime.bak &&

default_make &&

# restore the original /etc/localtime file
[ -f /etc/localtime.bak ] && mv -f /etc/localtime.bak /etc/localtime
