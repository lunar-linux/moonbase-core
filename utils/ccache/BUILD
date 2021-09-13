OPTS+=" -DZSTD_FROM_INTERNET=OFF -DHIREDIS_FROM_INTERNET=OFF"

if module_installed ccache ; then
   OPTS+=" -DUSE_CCACHE=ON"
 else
   OPTS+=" -DUSE_CCACHE=OFF"
fi &&

default_cmake_build

