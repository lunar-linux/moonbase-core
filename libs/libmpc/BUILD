(

  OPTS+=" --disable-static"  &&

  if [ -f /usr/lib/libmpc.so.2.0.0 ]; then
#    preserve the old version to prevent the crash of gcc
     cp /usr/lib/libmpc.so.2.0.0 /usr/lib/libmpc.so.2.0.0.old
   fi  &&

   default_build  &&

  if [ -f /usr/lib/libmpc.so.2.0.0.old ]; then
#    restore the old version to prevent the crash of gcc
     mv -f /usr/lib/libmpc.so.2.0.0.old /usr/lib/libmpc.so.2.0.0
     ln -sf /usr/lib/libmpc.so.2.0.0 /usr/lib/libmpc.so.2
   fi

) > $C_FIFO 2>&1
