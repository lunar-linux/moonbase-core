bad_flags -malign-double -s

OPTS+=" --without-bash-malloc \
        --with-curses \
        --without-installed-readline \
        --enable-static-link \
        --disable-profiling" &&

default_config &&
make version.h &&
make &&
prepare_install &&

cp -f bash /usr/bin/bash_static
