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

# figure out if removing the previous libncurses has killed gawk, and do
# a little hack to try to remedy the situation before trying to actually
# do the install

GAWK_NCURSES=$(ldd /bin/gawk |
    sed -n '/libncurses/{ s/^[ \t]*\([^ ][^ ]*\) .*/\1/;p }')

if [[ ! -z "$GAWK_HACK" && ! -e /lib/$GAWK_NCURSES ]]
then
    ln -s /lib/libncurses.so /lib/$GAWK_NCURSES
fi &&

make install

gather_docs ANNOUNCE TODO
