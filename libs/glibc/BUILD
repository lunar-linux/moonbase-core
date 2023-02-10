bad_flags ALL &&
unset LD_LIBRARY_PATH &&
unset _FORTIFY_SOURCE &&

cd glibc-build &&

echo "slibdir=/lib" > configparms &&

OPTS=" --host=$HOST" \
    " --build=$BUILD" \
    " --prefix=/usr" \
    " --libdir=/usr/lib" \
    " --infodir=/usr/share/info" \
    " --mandir=/usr/share/man" \
    " --sysconfdir=/etc" \
    " --with-elf" \
    " --enable-shared" \
    " --disable-profile" \
    " --with-headers=/usr/include" \
    " --disable-multiarch" \
    " --enable-obsolete-rpc" &&
    " --enable-bind-now" \
    " --enable-stack-protector=strong" \
    " --enable-stackguard-randomization" \
    " --disable-cet" \

../configure $OPTS &&

make
