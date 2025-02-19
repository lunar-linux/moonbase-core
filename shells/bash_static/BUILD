bad_flags -malign-double "-s "

OPTS+=" --bindir=/usr/bin \
        --with-curses \
	--disable-readline \
        --disable-profiling \
        --enable-static-link \
        --without-bash-mallocx"

GLIBC_MINOR_VERSION=$(lvu installed glibc | cut -f2 -d.)

if (( GLIBC_MINOR_VERSION >= 41 ))
then
	sedit '/CAN_REDEFINE_GETENV/s,^,// ,' config.h.in
fi

default_config &&
make version.h &&
make &&
prepare_install &&

cp -f bash /usr/bin/bash_static
