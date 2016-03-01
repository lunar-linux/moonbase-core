OPTS+=" --disable-static \
        --enable-cryptsetup-reencrypt" &&

default_build &&

# install hook
install -D -m644 $SCRIPT_DIRECTORY/encrypt_hook /usr/lib/initcpio/hooks/encrypt &&
install -D -m644 $SCRIPT_DIRECTORY/encrypt_install /usr/lib/initcpio/install/encrypt &&
install -D -m644 $SCRIPT_DIRECTORY/sd-encrypt /usr/lib/initcpio/install/sd-encrypt
