
  if [ -e /etc/init.d/sysctl.sh ]; then
    rm -f /etc/init.d/sysctl.sh  &&
    rm -f /etc/rcS.d/S99sysctl
  fi  &&

  if in_depends $MODULE systemd ; then
    OPTS+=" --with-systemd"
  fi &&

  OPTS+=" --prefix=/usr        \
          --exec-prefix=/      \
          --sysconfdir=/etc    \
          --libdir=/usr/lib    \
          --sbindir=/usr/bin   \
          --enable-skill       \
          --disable-static     \
          --enable-watch8bit" &&

  default_build &&

  if module_installed sysvinit; then
    cp $SCRIPT_DIRECTORY/init.d/sysctl /etc/init.d &&
    ln -sf ../init.d/sysctl /etc/rcS.d/S99sysctl
  fi  &&

  if [ ! -e /etc/sysctl.conf ] ; then
    install -g0 -o0 -m0600 $SCRIPT_DIRECTORY/sysctl.conf /etc
  fi
