# Do not remove --enable-debug=minimum, it will break some common
# API functions if debug is entirely disabled
export OPTS+=" --disable-fam \
               --disable-static \
               --enable-shared \
               --enable-debug=minimum" &&

AT_M4DIR=. autoreconf &&

default_build
