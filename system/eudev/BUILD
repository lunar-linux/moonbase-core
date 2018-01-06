sed -e 's/GROUP="dialout"/GROUP="uucp"/' \
    -e 's/GROUP="tape"/GROUP="storage"/' \
    -e 's/GROUP="cdrom"/GROUP="optical"/' \
    -i rules/*.rules &&

./autogen.sh &&

./configure --prefix=/usr \
            --with-rootprefix=/usr \
            --sysconfdir=/etc \
            --libdir=/usr/lib \
            --sbindir=/usr/bin \
            --enable-introspection \
            --enable-kmod \
            --enable-manpages \
            --enable-split-usr &&

default_make &&

rm -v /usr/include/libudev.h &&
rm -v /usr/lib/libudev*.{so*,a} &&

install -Dm644 $SCRIPT_DIRECTORY/initcpio_hooks /usr/lib/initcpio/hooks/udev &&
install -Dm644 $SCRIPT_DIRECTORY/initcpio_install /usr/lib/initcpio/install/udev &&
install -Dm644 $SCRIPT_DIRECTORY/udev-hwdb.hook /usr/share/libalpm/hooks/udev-hwdb.hook
