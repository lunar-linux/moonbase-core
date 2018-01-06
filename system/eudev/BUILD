./autogen.sh &&

./configure --prefix=/usr \
            --with-rootprefix=/usr \
            --sysconfdir=/etc \
            --libdir=/usr/lib \
            --enable-kmod \
            --enable-manpages &&

default_make &&

install -Dm644 $SCRIPT_DIRECTORY/initcpio_hooks /usr/lib/initcpio/hooks/udev &&
install -Dm644 $SCRIPT_DIRECTORY/initcpio_install /usr/lib/initcpio/install/udev &&
install -Dm644 $SCRIPT_DIRECTORY/udev-hwdb.hook /usr/share/libalpm/hooks/udev-hwdb.hook
