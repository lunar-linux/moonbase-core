# Build with DISPATCH=1 for runtime CPU feature detection
make PREFIX=/usr DISPATCH=1 &&

prepare_install &&

# Install with DISPATCH=1
make PREFIX=/usr DISPATCH=1 DESTDIR="" install &&

rm -f /usr/lib/libxxhash.a
