yes | ./Configure -n linux &&

make CC="cc ${CFLAGS} ${CPPFLAGS} ${LDFLAGS}" &&

prepare_install &&

install -Dm0755 lsof /usr/bin/ &&
install -Dm0644 Lsof.8 /usr/share/man/man8/lsof.8
