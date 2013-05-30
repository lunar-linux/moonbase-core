patch_it $SOURCE2 0 &&
patch_it $SOURCE3 1 &&

sedit "/^MAN_DIR/s/.*/MAN_DIR=\/usr\/share\/man/;/manpath/d" Makefile  &&
make ROOT= all   &&
prepare_install  &&
make ROOT= install
