(

  patch_it $SOURCE_CACHE/$SOURCE2 1  &&

  export FORCE_UNSAFE_CONFIGURE=1  &&

  bad_flags -malign-double  &&

  # We really want this
  OPTS+=" --enable-largefile"  &&

  if [ "$WITH_NLS" == "y" ]; then
    OPTS+=" --enable-nls"
  else
    OPTS+=" --disable-nls"
  fi  &&

  # This option resolves conflicts with shadow/heimdal, net-tools and procps
  OPTS+=" --enable-no-install-program=arch,hostname,su,groups,kill,uptime"  &&

  DEFAULT_POSIX2_VERSION=199209 default_build &&

  # for systems without /bin -> /usr/bin symlink
  if [ "`cd /usr/bin; pwd -P`" != "`cd /bin; pwd -P`" ]; then
    ln -sf /usr/bin/pwd /bin/pwd  &&
    ln -sf /usr/bin/ln /bin/ln
  fi

) > $C_FIFO 2>&1
