bad_flags -malign-double -s

OPTS+=" --bindir=/usr/bin \
        --with-curses \
        --disable-profiling \
        --enable-static-link \
        --without-bash-malloc \
        --without-installed-readline"

default_config &&
make version.h &&
make &&
prepare_install &&

cp -f bash /usr/bin/bash_static
