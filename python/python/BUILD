OPTS+=" --enable-shared \
        --enable-ipv6 \
        --with-threads \
        --with-system-ffi \
        --with-system-expat \
        --with-computed-gotos \
        --without-ensurepip"

_BASEVER=${VERSION%.*}
DESTDIR=${DESTDIR:-$SOURCE_DIRECTORY/__pythondest3}
mkdir -p $DESTDIR &&

default_config &&
make EXTRA_CFLAGS="$CFLAGS" &&

# Avoid rebuild on make install
sedit 's;^all:.*$;all: build_all;' Makefile &&
make DESTDIR="$DESTDIR" EXTRA_CFLAGS="$CFLAGS" install &&

# Convenience symlinks
ln -sf python3 "$DESTDIR"/usr/bin/python &&
ln -sf python3-config "$DESTDIR"/usr/bin/python-config &&
ln -sf idle3 "$DESTDIR"/usr/bin/idle &&
ln -sf pydoc3 "$DESTDIR"/usr/bin/pydoc &&
ln -sf python${_BASEVER}.1 "$DESTDIR"/usr/share/man/man1/python.1 &&
ln -sf python-${_BASEVER}.pc "$DESTDIR"/usr/lib/pkgconfig/python3.pc &&

install -dm755 "$DESTDIR"/usr/lib/python${_BASEVER}/Tools/{i18n,scripts} &&
install -m755 $SOURCE_DIRECTORY/Tools/i18n/{msgfmt,pygettext}.py "$DESTDIR"/usr/lib/python${_BASEVER}/Tools/i18n/ &&
install -m755 $SOURCE_DIRECTORY/Tools/scripts/{README,*.py} "$DESTDIR"/usr/lib/python${_BASEVER}/Tools/scripts/ &&

prepare_install &&
if [[ ${DESTDIR_BUILD:-n} = n ]]
then
    find $DESTDIR/usr/bin &&
    cp -rfv --remove-destination "$DESTDIR"/* /
fi
