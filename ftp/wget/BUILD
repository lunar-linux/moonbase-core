# setting the ssl option
if in_depends $MODULE openssl && module_installed "openssl" ; then
    OPTS+=" --with-ssl=openssl"
elif in_depends $MODULE libressl  && module_installed "libressl" ; then
    OPTS+=" --with-ssl=openssl"
elif in_depends $MODULE gnutls && module_installed "gnutls" ; then
    OPTS+=" --with-ssl"
else
    OPTS+=" --without-ssl"
fi &&

OPTS+=" --disable-debug"  &&

default_build
