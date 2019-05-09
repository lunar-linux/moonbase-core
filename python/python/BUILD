OPTS+=" --enable-shared \
        --enable-ipv6 \
        --with-threads \
        --with-system-ffi \
        --with-system-expat \
        --with-computed-gotos \
        --without-ensurepip"

_BASEVER=${VERSION%.*}
_PYDESTDIR=$SOURCE_DIRECTORY/__pythondest3
mkdir -p $_PYDESTDIR &&

default_config &&
make build_all EXTRA_CFLAGS="$CFLAGS" &&

# Avoid rebuild on make install
sedit 's;^all:.*$;all: build_all;' Makefile &&
make DESTDIR="$_PYDESTDIR" EXTRA_CFLAGS="$CFLAGS" install &&

# Convenience symlinks
ln -sf python3 "$_PYDESTDIR"/usr/bin/python &&
ln -sf python3-config "$_PYDESTDIR"/usr/bin/python-config &&
ln -sf idle3 "$_PYDESTDIR"/usr/bin/idle &&
ln -sf pydoc3 "$_PYDESTDIR"/usr/bin/pydoc &&
ln -sf python${_BASEVER}.1 "$_PYDESTDIR"/usr/share/man/man1/python.1 &&
ln -sf python-${_BASEVER}.pc "$_PYDESTDIR"/usr/lib/pkgconfig/python3.pc &&

install -dm755 "$_PYDESTDIR"/usr/lib/python${_BASEVER}/Tools/{i18n,scripts} &&
install -m755 $SOURCE_DIRECTORY/Tools/i18n/{msgfmt,pygettext}.py "$_PYDESTDIR"/usr/lib/python${_BASEVER}/Tools/i18n/ &&
install -m755 $SOURCE_DIRECTORY/Tools/scripts/{README,*.py} "$_PYDESTDIR"/usr/lib/python${_BASEVER}/Tools/scripts/ &&

prepare_install &&
cp -rfv --remove-destination "$_PYDESTDIR"/* /
