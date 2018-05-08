#!/bin/bash
# Seems that ncurses-5.5 has problems with garbage in /usr/share/terminfo
# Note: ncurses-5.5 also has all the "screen" files for terminfo, so no
# recompile is needed
rm -rf /usr/share/terminfo &&

# ************************ WARNING *************************
# DO NOT MESS WITH THE CONFIGURE STUFF here unless you
# really know what you're doing! We chose the lib location
# specifically so we could link ncurses to bash which is
# needed at init time! If you move it you could break your
# system!
unset CC CXX &&

# Attempt to preserve whatever version of ncurses gawk uses, if gawk is linked
# with ncurses

GAWK_NCURSES=$(ldd /bin/gawk |
    sed -n '/libncurses/{ s/^[ \t]*\([^ ][^ ]*\) .*/\1/;p }')

if [[ ! -z $GAWK_NCURSES ]]
then
    cp /lib/$GAWK_NCURSES /lib/lunar-$GAWK_NCURSES
fi &&

OPTS+=" PKG_CONFIG_LIBDIR=/usr/lib/pkgconfig" &&

set -x &&
./configure  --build=$BUILD                           \
             --prefix=/usr                            \
             --libdir=/lib                            \
             --mandir=/usr/share/man                  \
             --disable-termcap                        \
             --enable-pc-files                        \
             --enable-colorfgbg                       \
             --without-ada                            \
             --without-debug                          \
             --with-normal                            \
             --with-shared                            \
             --with-manpage-format=gzip               \
             --with-terminfo-dirs=/usr/share/terminfo \
             $OPTS                                   &&

default_make &&

devoke_installwatch &&
set +x &&

# Now to make ncurses wide
make clean &&

unset CC CXX &&

set -x &&
./configure  --build=$BUILD                           \
             --prefix=/usr                            \
             --libdir=/lib                            \
             --includedir=/usr/include/ncursesw       \
             --mandir=/usr/share/man                  \
             --disable-termcap                        \
             --enable-colorfgbg                       \
             --enable-widec                           \
             --enable-pc-files                        \
             --without-ada                            \
             --without-debug                          \
             --with-normal                            \
             --with-shared                            \
             --with-manpage-format=gzip               \
             --with-terminfo-dirs=/usr/share/terminfo \
            $OPTS                                    &&

set +x &&

make &&

prepare_install &&

if [[ ! -z $GAWK_NCURSES ]]
then
    mv /lib/lunar-$GAWK_NCURSES /lib/$GAWK_NCURSES
fi &&

make install &&

gather_docs ANNOUNCE TODO
