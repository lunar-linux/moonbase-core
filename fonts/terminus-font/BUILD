OPTS+=' --psfdir=/usr/share/kbd/consolefonts \
        --x11dir=/usr/share/fonts/misc' &&
chmod +x configure &&

default_build &&

install -d /etc/fonts/conf.avail &&
install -Dm644 75-yes-terminus.conf /etc/fonts/conf.avail/75-yes-terminus.conf &&

install -d /etc/fonts/conf.d &&
cd /etc/fonts/conf.d &&
ln -s ../conf.avail/75-yes-terminus.conf .
