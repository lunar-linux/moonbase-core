CFLAGS+=" -ffat-lto-objects"

# We need to add this program prefix else its binaries will conflict with binutils
OPTS+=" --program-prefix=eu- \
        --disable-debuginfod \
        --disable-libdebuginfod \
        --disable-valgrind \
        --enable-deterministic-archives \
        --with-zlib"

default_build
