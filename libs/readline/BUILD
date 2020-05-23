# ************************ WARNING *************************
# DO NOT MESS WITH THE CONFIGURE STUFF here unless you
# really know what you're doing! We chose the lib location
# specifically so we could link readline to bash which is
# needed at init time! If you move it you could break your
# system!

./configure --libdir=/lib \
            --prefix=/usr \
            --mandir=/usr/share/man \
            --infodir=/usr/share/info \
            --disable-static &&

make SHLIB_LIBS=-lncurses &&
prepare_install &&
make install &&

if [ ! -e /etc/inputrc ]; then
  install $SCRIPT_DIRECTORY/inputrc /etc/
fi
