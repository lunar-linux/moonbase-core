default_config &&

if ! make ${MAKES:-j${MAKES}}
then
  ./build.sh &&
  prepare_install &&
  ./make install
else
  prepare_install &&
  make install
fi
