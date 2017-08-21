unset CPP CXX CC CFLAGS CXXFLAGS CPPFLAGS LDFLAGS &&

./autogen.sh

OPTS+=" --enable-nls \
        --enable-mm-debug \
        --enable-boot-time \
        --enable-cache-stats \
        --disable-werror \
        --with-grubdir=grub \
        --with-bootdir=/boot" &&

OPTS+=" --sbindir=/usr/bin" &&

if in_depends $MODULE efibootmgr; then
    [[ 'arch' == "x86_64" ]] && EFIARCH="x86_64"
    [[ 'arch' == "i686" ]] && EFIARCH="i386"
    OPTS+=" --disable-efiemu --target=$EFIARCH"
else
    # Set dependent variables for BIOS build
    if [ 'arch' == "x86_64" ]; then
         OPTS+=" --enable-efiemu"
    else
         OPTS+=" --disable-efiemu"
    fi
fi &&

default_build
