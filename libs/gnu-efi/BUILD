# upstream compiles with -mno-sse
bad_flags -mfpmath=sse -mfpmath=both &&

if [[ "$(arch)" == "x86_64" ]]; then
  EFI_ARCH=x86_64
elif [[ "$(arch)" == "aarch64" ]]; then
  EFI_ARCH=aarch64
else
  EFI_ARCH=ia32
fi &&

# Lunar's LDFLAGS don't get along well with gnu-efi, so clear them out
unset LDFLAGS &&

make lib gnuefi inc apps &&
prepare_install &&
make PREFIX="/usr" LIBDIR="/usr/lib" install &&

install -d "/usr/share/gnu-efi/apps/${EFI_ARCH}/" &&
install -D -m0644 "${EFI_ARCH}/apps"/*.efi "/usr/share/gnu-efi/apps/${EFI_ARCH}/" &&

sedit 's@/local@@g' /usr/lib/pkgconfig/gnu-efi.pc
