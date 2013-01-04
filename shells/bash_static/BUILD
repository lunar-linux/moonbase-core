(

   bad_flags -malign-double -s

  patch_it $SOURCE2  0  &&
  patch_it $SOURCE3  0  &&
  patch_it $SOURCE4  0  &&
  patch_it $SOURCE5  0  &&
  patch_it $SOURCE6  0  &&
  patch_it $SOURCE7  0  &&
  patch_it $SOURCE8  0  &&
  patch_it $SOURCE9  0  &&
  patch_it $SOURCE10 0  &&
  patch_it $SOURCE11 0  &&
  patch_it $SOURCE12 0  &&
  patch_it $SOURCE13 0  &&
  patch_it $SOURCE14 0  &&
  patch_it $SOURCE15 0  &&
  patch_it $SOURCE16 0  &&
  patch_it $SOURCE17 0  &&
  patch_it $SOURCE18 0  &&
  patch_it $SOURCE19 0  &&
  patch_it $SOURCE20 0  &&
  patch_it $SOURCE21 0  &&
  patch_it $SOURCE22 0  &&
  patch_it $SOURCE23 0  &&
  patch_it $SOURCE24 0  &&
  patch_it $SOURCE25 0  &&
  patch_it $SOURCE26 0  &&
  patch_it $SOURCE27 0  &&
  patch_it $SOURCE28 0  &&
  patch_it $SOURCE29 0  &&
  patch_it $SOURCE30 0  &&
  patch_it $SOURCE31 0  &&
  patch_it $SOURCE32 0  &&
  patch_it $SOURCE33 0  &&
  patch_it $SOURCE34 0  &&
  patch_it $SOURCE35 0  &&
  patch_it $SOURCE36 0  &&
  patch_it $SOURCE37 0  &&
  patch_it $SOURCE38 0  &&
  patch_it $SOURCE39 0  &&
  patch_it $SOURCE40 0  &&
  patch_it $SOURCE41 0  &&
  patch_it $SOURCE42 0  &&
  patch_it $SOURCE43 0  &&

   OPTS+=" --bindir=/bin                 \
           --without-bash-malloc         \
           --without-installed-readline  \
           --with-curses                 \
           --enable-static-link          \
           --disable-profiling"         &&

   default_config   &&
   make version.h   &&
   make             &&
   prepare_install  &&

   cp -f bash /bin/bash_static

) > $C_FIFO 2>&1
