OPTS+=" -DEXPAT_BUILD_DOCS=OFF \
        -DEXPAT_BUILD_TESTS=OFF \
        -DEXPAT_BUILD_EXAMPLES=OFF"

default_cmake_build &&

# Let's be naughty and do the coverup
ln -sf /usr/lib/libexpat.so /usr/lib/libexpat.so.0
