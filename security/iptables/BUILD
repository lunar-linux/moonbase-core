# save tables
if module_installed iptables; then
  iptables-save -c > /etc/config.d/iptables.sav
fi &&

# headers aren't installed by default
OPTS+=" --enable-libipq --enable-devel" &&

default_build &&

# revive tables
if [ -f /etc/config.d/iptables.sav ]; then
  cat /etc/config.d/iptables.sav | iptables-restore -c &&
  rm /etc/config.d/iptables.sav
fi &&

# add empty iptables file for flushing
if [ ! -f /etc/config.d/iptables-empty ]; then
  [ ! -d /etc/config.d ] && mkdir -p /etc/config.d
  cp $SCRIPT_DIRECTORY/files/iptables-empty /etc/config.d/iptables-empty
fi &&

# little wrapper for systemd's usage
# todo: should be detected by our package-management (installwatch?)
#       tho i guess nobody uses lunar without installed iptables..
if [ ! -f /usr/sbin/iptsave ]; then
  cp $SCRIPT_DIRECTORY/files/iptsave /usr/sbin/iptsave &&
  chmod a+x /usr/sbin/iptsave
fi
