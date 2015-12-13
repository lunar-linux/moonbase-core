# setting the ssl option
if in_depends $MODULE openssl && module_installed "openssl"; then
  OPTS+=" --with-openssl --without-gnutls"
elif in_depends $MODULE gnutls && module_installed "gnutls"; then
  OPTS+=" --with-gnutls --without-openssl"
else
  OPTS+=" --without-openssl --without-gnutls"
fi &&

default_build
