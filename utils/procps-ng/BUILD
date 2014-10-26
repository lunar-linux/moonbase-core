
  OPTS+=" --enable-skill" &&

  if in_depends $MODULE systemd ; then
    OPTS+=" --with-systemd"
  fi &&

  if [ ! -e /etc/sysctl.conf ] ; then
    install -g0 -o0 -m0600 $SCRIPT_DIRECTORY/sysctl.conf /etc
  fi
