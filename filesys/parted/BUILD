OPTS+=" --disable-rpath \
        --disable-debug \
        --disable-static" &&

default_config &&

sedit "s:-1.14::" Makefile &&

default_make &&

gather_docs ABOUT-NLS BUGS THANKS doc/API doc/FAQ doc/FAT doc/USER.jp
