# setting the ssl option
if in_depends $MODULE openssl || in_depends $MODULE libressl; then
  OPTS+=" --with-ssl=openssl"
elif in_depends $MODULE gnutls; then
  OPTS+=" --with-ssl"
else
  OPTS+=" --without-ssl"
fi

OPTS+=" --disable-debug"

default_build
