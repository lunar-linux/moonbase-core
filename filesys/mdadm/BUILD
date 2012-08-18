(
   if module_installed systemd; then
      sedit 's@/lib/udev/rules.d/64-md-raid.rules@/usr\0@' Makefile
   fi  &&

   default_make

) > $C_FIFO 2>&1
