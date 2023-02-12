bad_flags ALL &&
unset LD_LIBRARY_PATH &&
unset _FORTIFY_SOURCE &&

cd glibc-build &&

echo "slibdir=/lib" > configparms &&

OPTS=" --host=$HOST \
    --build=$BUILD \
    --prefix=/usr \
    --libdir=/usr/lib \
    --infodir=/usr/share/info \
    --mandir=/usr/share/man \
    --sysconfdir=/etc \
    --with-elf \
    --disable-werror \
    --enable-shared \
    --disable-profile \
    --with-headers=/usr/include \
    --disable-multiarch \
    --enable-obsolete-rpc \
    --enable-bind-now \
    --enable-stack-protector=strong \
    --enable-stackguard-randomization \
    --disable-cet" &&

../configure $OPTS &&

make &&

prepare_install &&

mkdir $SOURCE_DIRECTORY/glibc-build/old.libs  &&
message "${MESSAGE_COLOR}Copying old libraries${DEFAULT_COLOR}" &&
for file in /lib; do
    if [ -f "$file" ]; then
        cp -a "$file" $SOURCE_DIRECTORY/glibc-build/old.libs
    fi
done &&

#message "${MESSAGE_COLOR}Running ldconfig${DEFAULT_COLOR}" &&
#ldconfig $SOURCE_DIRECTORY/glibc-build/old.libs &&
#export_ld $SOURCE_DIRECTORY/glibc-build/old.libs &&

#message "${MESSAGE_COLOR}Changing ld-linux${DEFAULT_COLOR}" &&
#for each in /lib/ld-linux*; do
#    if [ -f "$each" ]; then
#        LD=$(readlink "$each")
#	LDB=${LD##*/}
#	ln -sfv $SOURCE_DIRECTORY/glibc-build/old.libs/$LDB "$each"
#    fi
#done &&

cd $SOURCE_DIRECTORY/glibc-build &&

message "${MESSAGE_COLOR}Removing glibc${DEFAULT_COLOR}" &&
#lrm --no-sustain glibc &&

# glibc only installs those if the file differs
for file in ${INSTALL_ROOT}/usr/include/bits/syscall.h \
    ${INSTALL_ROOT}/usr/include/gnu/stubs.h \
    ${INSTALL_ROOT}/usr/include/gnu/stubs-32.h \
    ${INSTALL_ROOT}/usr/include/gnu/stubs-64.h; do
    if [ -f "$file" ]; then
        rm -vf $file
    fi
done &&

message "${MESSAGE_COLOR}Running 'make install'${DEFAULT_COLOR}" &&
make install install_root="${INSTALL_ROOT}"
message "${MESSAGE_COLOR}Done installing${DEFAULT_COLOR}"
