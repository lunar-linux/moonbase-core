(
#still need several patches

  OPTS+=" --enable-arch --enable-agetty --disable-kill \
          --disable-last --disable-mesg --enable-partx --enable-raw \
          --enable-rename --disable-reset --disable-login-utils \
          --enable-schedutils --disable-wall --enable-write --enable-fsck"  &&

  default_build  &&

  install -g0 -o0 -m755 $SCRIPT_DIRECTORY/make-issue /sbin/make-issue

) > $C_FIFO 2>&1
