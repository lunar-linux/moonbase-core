./autogen.sh &&

OPTS+=" --exec-prefix=/usr \
        --sysconfdir=/etc  \
        --sbindir=/usr/bin \
        --disable-static"

default_build &&

if [ ! -e /etc/sysctl.d/sysctl.conf ]; then
  install -g0 -o0 -m0600 $SCRIPT_DIRECTORY/sysctl.conf /etc/sysctl.d
fi &&

if in_depends $MODULE systemd && [ ! -e /etc/sysctl.d/99-sysctl.conf ]; then
  mv /etc/sysctl.d/sysctl.conf /etc/sysctl.d/99-sysctl.conf
else
  install -g0 -o0 -m0600 $SCRIPT_DIRECTORY/sysctl.conf /etc/sysctl.d/99-sysctl.conf
fi
