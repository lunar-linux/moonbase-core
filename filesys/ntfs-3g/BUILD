sed 's|$(DESTDIR)/sbin|$(DESTDIR)/usr/bin|' -i {ntfsprogs,src}/Makefile.in &&

OPTS+=" --enable-extras     \
        --sbin=/usr/bin     \
        --enable-ntfsprogs  \
        --disable-ldconfig  \
        --disable-static    \
        --mandir=/usr/share/man \
        --without-hd  \
        --exec-prefix=/usr" &&

default_build
