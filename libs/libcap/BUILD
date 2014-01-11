(

   patch_it $SOURCE_CACHE/$SOURCE2 1  &&

   sedit "s/uapi\///" libcap/Makefile  &&

  # no static libs
  sedit "s/all: \$(MINLIBNAME) \$(STALIBNAME)/all: \$(MINLIBNAME)/g" libcap/Makefile  &&
  sedit "/install -m 0644 \$(STALIBNAME)/d"                          libcap/Makefile  &&

  default_make

) > $C_FIFO 2>&1
