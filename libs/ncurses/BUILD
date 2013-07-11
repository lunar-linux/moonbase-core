(

# Seems that ncurses-5.5 has problems with garbage in /usr/share/terminfo
# Note: ncurses-5.5 also has all the "screen" files for terminfo, so no recompile is needed
  rm -rf /usr/share/terminfo  &&

# ************************ WARNING *************************
# DO NOT MESS WITH THE CONFIGURE STUFF here unless you
# really know what you're doing! We chose the lib location
# specifically so we could link ncurses to bash which is
# needed at init time! If you move it you could break your
# system!
  unset CC CXX &&

  OPTS+=" PKG_CONFIG_LIBDIR=/usr/lib/pkgconfig" &&

  set -x &&
  ./configure  --build=$BUILD                            \
               --prefix=/usr                             \
               --libdir=/lib                             \
               --with-normal                             \
               --with-shared                             \
               --mandir=/usr/share/man                   \
               --with-manpage-format=gzip                \
               --disable-termcap                         \
               --enable-colorfgbg                        \
               --with-terminfo-dirs=/usr/share/terminfo  \
               --enable-pc-files                         \
               $OPTS                                    &&

  default_make &&

  devoke_installwatch &&

  set +x &&

# Now to make nucurses wide
  make clean &&

  unset CC CXX  &&

  set -x &&
  ./configure  --build=$BUILD                            \
               --prefix=/usr                             \
               --libdir=/lib                             \
               --with-normal                             \
               --with-shared                             \
               --includedir=/usr/include/ncursesw        \
               --mandir=/usr/share/man                   \
               --with-manpage-format=gzip                \
               --disable-termcap                         \
               --enable-colorfgbg                        \
               --with-terminfo-dirs=/usr/share/terminfo  \
               --enable-widec                            \
               --enable-pc-files                         \
               $OPTS                                    &&

  set +x &&
  default_make &&
  ln -sf /usr/include/ncursesw /usr/include/ncurses  &&
  gather_docs ANNOUNCE TODO

) > $C_FIFO 2>&1
