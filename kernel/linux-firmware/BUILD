(

  prepare_install &&
  mkdir -p /lib/firmware  &&
  cp -av * /lib/firmware &&
  rm -f /lib/firmware/{GPL*,LICEN*,WHENCE} &&

  gather_docs GPL* LICEN* WHENCE

) > $C_FIFO 2>&1
