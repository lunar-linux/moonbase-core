(
  ./configure  -prefix=/usr  \
              $OPTS         &&

  sedit 's:${exec_prefix}/lib/python:/usr/lib/python:' python/Makefile  &&
  sedit 's:${prefix}/lib/python:/usr/lib/python:'      python/Makefile  &&

  default_make  &&
  make dict

) > $C_FIFO 2>&1
