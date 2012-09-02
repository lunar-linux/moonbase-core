(

  ./configure  -prefix=/usr     \
              --without-python  \
              $OPTS            &&

  default_make  &&
  make dict

) > $C_FIFO 2>&1
