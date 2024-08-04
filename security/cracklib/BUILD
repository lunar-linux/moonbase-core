OPTS+=" --exec-prefix=/usr --without-python"

default_build &&

mkdir -p /usr/share/dict &&
ln -sf /usr/share/cracklib/cracklib-small /usr/share/dict/cracklib-small &&
sh ./util/cracklib-format dicts/cracklib-small | sh ./util/cracklib-packer /usr/share/cracklib/pw_dict
