OPTS+=" --enable-shared \
        --enable-ipv6 \
        --with-threads \
        --with-system-ffi \
        --with-system-expat \
        --with-computed-gotos \
        --without-ensurepip" &&

default_config &&

# This is important, lets 2.x versions and it to coexist.
make EXTRA_CFLAGS="$CFLAGS" &&
prepare_install &&
make install EXTRA_CFLAGS="$CFLAGS" &&

ln -sf python3 /usr/bin/python &&
ln -sf python3-config /usr/bin/python-config &&
ln -sf idle3 /usr/bin/idle &&
ln -sf pydoc3 /usr/bin/pydoc &&
ln -sf python3.6.1 /usr/share/man/man1/python.1
