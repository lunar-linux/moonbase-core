# libcom_err.a(error_message.o): relocation R_X86_64_32 against `.bss' can not be used when making a shared object; recompile with -fPIC
CFLAGS+=" -fPIC" &&

#the dvi documentation fails to build with current texlive
sedit 's/$(DVI)/#/' doc/Makefile.in &&

OPTS+=" --build=$BUILD      \
        --with-root-prefix= \
        --enable-elf-shlibs \
        --disable-libuuid   \
        --disable-uuidd     \
        --disable-libblkid  \
        --disable-fsck"    &&

default_build &&

make install-libs || exit 1
