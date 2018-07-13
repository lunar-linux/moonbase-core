unset CPP CXX CC CFLAGS CXXFLAGS CPPFLAGS LDFLAGS MAKEFLAGS &&

if [ "$(arch)" == "x86_64" ]; then
  _EFI_ARCH="x86_64"
  _EFI_EMU="--enable-efiemu"
else
  _EFI_ARCH="i386"
  _EFI_EMU="--disable-efiemu"
fi &&

OPTS+=" --prefix=/usr \
        --bindir=/usr/bin \
        --sbindir=/usr/bin \
        --mandir=/usr/share/man \
        --infodir=/usr/share/info \
        --datarootdir=/usr/share \
        --sysconfdir=/etc \
        --enable-nls \
        --enable-mm-debug \
        --enable-boot-time \
        --enable-cache-stats \
        --with-bootdir=/boot \
        --with-grubdir=grub \
        --disable-silent-rules \
        --disable-werror" &&

GRUB_BIOS=$SOURCE_DIRECTORY/grub-bios &&
mkdir -p $GRUB_BIOS &&
cd $GRUB_BIOS  &&
../configure --with-platform="pc" \
             --target="i386" \
             ${_EFI_EMU} \
             $OPTS &&
make &&

GRUB_EFI=$SOURCE_DIRECTORY/grub-efi &&
mkdir -p $GRUB_EFI &&
cd $GRUB_EFI &&
../configure --with-platform="efi" \
             --target="${_EFI_ARCH}" \
             --disable-efiemu \
             $OPTS &&
make &&

prepare_install &&
cd $GRUB_BIOS &&
make bashcompletiondir=/usr/share/bash-completion/completions install &&
cd $GRUB_EFI &&
make bashcompletiondir=/usr/share/bash-completion/completions install &&

# Clean up some debug files etc
(rm -f /usr/lib/grub/{i386-pc,${_EFI_ARCH}-efi}/{*.module,*.image,kernel.exec,gdb_grub,gmodule.pl} || true)
