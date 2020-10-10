# preserve the existing /etc/localtime symlink
if [ -f /etc/localtime ]; then
  mv -f /etc/localtime /etc/localtime.tmp.bak
fi &&

default_make &&

# This creates the posixrules file. We use New York because POSIX requires the
# daylight savings time rules to be in accordance with US rules
zic -b fat -d /usr/share/zoneinfo -p America/New_York &&

# restore the original /etc/localtime file
if [ -f /etc/localtime.tmp.bak ]; then
  mv -f /etc/localtime.tmp.bak /etc/localtime
fi
