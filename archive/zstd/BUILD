cd build/cmake

OPTS+=" -DCMAKE_BUILD_TYPE=Release \
        -DCMAKE_INSTALL_PREFIX=/usr \
        -DCMAKE_INSTALL_LIBDIR=lib \
        -DZSTD_ZLIB_SUPPORT=ON \
        -DZSTD_LZ4_SUPPORT=ON \
        -DZSTD_BUILD_CONTRIB=ON \
        -DZSTD_BUILD_STATIC=OFF \
        -DZSTD_BUILD_TESTS=OFF \
        -DZSTD_PROGRAMS_LINK_SHARED=ON \
        -Wno-dev"

cmake -B $MODULE-$VERSION -S . -G Ninja $OPTS &&
cmake --build $MODULE-$VERSION &&

prepare_install
cmake --install $MODULE-$VERSION
