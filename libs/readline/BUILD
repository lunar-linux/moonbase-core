# Real and working fix for readline major version upgrade
mkdir -p /tmp/old.libraries &&
cp -f /lib/libreadline.so.* /tmp/old.libraries &&
cp -f /lib/libhistory.so.*  /tmp/old.libraries &&
LD_LIBRARY_PATH=/tmp/old.libraries:$LD_LIBRARY_PATH &&

OUR_OLD_READLINE_VVV=$(lvu installed readline | sed -r 's/([0-9]+).+/\1/') &&
set_module_config OUR_OLD_READLINE_VVV "$OUR_OLD_READLINE_VVV" &&

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
