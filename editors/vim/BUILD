OPTS+=" --with-features=huge \
        --enable-multibyte \
        --enable-cscope \
        --enable-netbeans \
        --enable-acl" &&

# otherwise it defaults to auto/x+gtk
if ! in_depends $MODULE gtk+-3; then
  OPTS+=" --enable-gui=no --without-x"
fi &&

cd src &&

default_config &&
make &&
prepare_install &&

rm -f /usr/bin/vim /usr/bin/vi  &&
(find -L /usr/bin -samefile /usr/bin/vim -delete || true) &&
( find /usr/share/vim -type d -exec rmdir {} \; &> /dev/null || true) &&

make -j1 install &&

install -Dm644 $SOURCE_DIRECTORY/runtime/ftplugin/logtalk.dict /usr/share/vim/vim${MAJOR}/ftplugin/logtalk.dict &&

ln -sf /usr/bin/vim /usr/bin/vi &&
install -Dm644 $SCRIPT_DIRECTORY/vimrc /usr/share/vim/vim${MAJOR}/sample.vimrc &&
[ -f /etc/vimrc ] || install -Dm644 $SCRIPT_DIRECTORY/vimrc /etc/ &&

# $SCRIPT_DIRECTORY/skel/.config doesn't get installed by lunar, so do this here
install -Dm644 $SCRIPT_DIRECTORY/skel/.config/vim/vimrc /etc/skel/.config/vim/vimrc
