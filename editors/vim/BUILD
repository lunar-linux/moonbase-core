OPTS+=" --with-features=huge --enable-cscope --enable-fail-if-missing" &&

# otherwise it defaults to auto/x+gtk
if ! in_depends $MODULE gtk+-3 && ! in_depends $MODULE gtk+-2; then
  OPTS+=" --enable-gui=no --without-x"
fi &&


cd src &&

default_config &&
make &&
prepare_install &&

rm -f /usr/bin/vim /usr/bin/vi  &&
( find /usr/share/vim -type d -exec rmdir {} \; &> /dev/null || true) &&

make install &&

ln -sf /usr/bin/vim /usr/bin/vi &&
cp -f $SCRIPT_DIRECTORY/vimrc /usr/share/vim/vim${MAJOR}/sample.vimrc
