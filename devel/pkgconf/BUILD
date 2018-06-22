OPTS+=" --with-pkg-config-dir=/usr/lib/pkgconfig:/usr/share/pkgconfig \
        --with-system-libdir=/usr/lib \
        --with-system-includedir=/usr/include \
        --disable-static"

default_build &&

ln -sf /usr/bin/pkgconf /usr/bin/pkg-config &&
ln -sf /usr/share/man/man1/pkgconf.1 /usr/share/man/man1/pkg-config.1
