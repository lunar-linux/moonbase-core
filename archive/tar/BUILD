export FORCE_UNSAFE_CONFIGURE=1  &&
cp $SOURCE_CACHE/$SOURCE2 tar.1.gz  &&

# this sedit restores the tar --list to its older 1.15.1 format
sedit "s/tartime (st->mtime, false)/tartime (st->mtime, true)/" src/list.c  &&

# Fixes an incompatibility with glibc-2.16
sedit '/gets is a/d' gnu/stdio.in.h  &&

default_build &&

install -c -m644 tar.1.gz /usr/share/man/man1
