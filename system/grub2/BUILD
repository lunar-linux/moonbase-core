(
  
  unset CPP CXX CC CFLAGS CXXFLAGS CPPFLAGS LDFLAGS  &&
  
  OPTS+=" --with-platform="pc" \
    --enable-mm-debug \
    --enable-nls \
    --enable-cache-stats \
    --enable-grub-mkfont \
    --disable-werror \
    --with-bootdir=/boot \
    --with-grubdir=grub " &&
  
  default_build
  
) > $C_FIFO 2>&1
