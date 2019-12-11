if [[ "$(arch)" == "x86_64" ]]; then
  EFI_ARCH=x86_64
else
  EFI_ARCH=ia32
fi &&

# build uses LDFLAGS with `ld` binary, so trim lunar's options
export LDFLAGS="$(echo $LDFLAGS | sed 's/-Wl,//g; s/-O1,//g')" &&

make lib gnuefi inc apps &&
prepare_install &&
make PREFIX="/usr" LIBDIR="/usr/lib" install &&

install -d "/usr/share/gnu-efi/apps/${EFI_ARCH}/" &&
install -D -m0644 "${EFI_ARCH}/apps"/*.efi "/usr/share/gnu-efi/apps/${EFI_ARCH}/"
