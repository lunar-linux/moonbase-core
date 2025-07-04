./autogen.sh &&
sed 's|$(DESTDIR)/sbin|$(DESTDIR)/usr/bin|' -i {ntfsprogs,src}/Makefile.in &&
autoreconf -fiv &&
#export LIBGCRYPT_LIBS="-lgcrypt"

# Use fuse internal,see https://bugs.gentoo.org/822024
OPTS+=" --enable-extras     \
        --with-uuid \
        --enable-ntfsprogs  \
        --disable-ldconfig  \
        --disable-static    \
        --enable-posix-acls \
        --enable-xattr-mappings \
        --mandir=/usr/share/man \
        --sbin=/usr/bin \
        --without-hd \
        --with-fuse=internal \
        --exec-prefix=/usr" &&

default_build
