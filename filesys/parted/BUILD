OPTS+=" --disable-rpath \
        --disable-static"

sedit '/am__api_version/s/17/18/' configure &&

default_config &&

default_make &&

gather_docs ABOUT-NLS BUGS THANKS doc/API doc/FAQ doc/FAT doc/USER.jp
