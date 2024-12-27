default_meson_build &&

# Install a missing command
install -vDm 755 $MODULE-$VERSION/usbreset /usr/bin/ &&
install -vDm 644 man/usbreset.1 /usr/share/man/man1/ &&

gunzip $SOURCE_CACHE/$SOURCE2 -c > usb.ids &&
{ rm -f /usr/share/usb.ids* || true; } &&
install -vDm644 usb.ids /usr/share/ &&

# The next line makes sure you will get a fresh usb id's db
# everytime you lin usbutils:
rm -f $SOURCE_CACHE/$SOURCE2
