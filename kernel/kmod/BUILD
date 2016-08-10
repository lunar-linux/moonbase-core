OPTS+=" --exec-prefix=/usr --with-zlib" &&

OPTS+=" --sbindir=/usr/bin" &&

default_build &&

install -dm755 /{etc,usr/lib}/{depmod,modprobe}.d &&

# add symlinks to kmod
ln -sf /usr/bin/kmod /usr/bin/lsmod &&
for tool in {ins,rm,dep}mod mod{info,probe}; do
#  ln -sf /usr/bin/kmod /usr/sbin/$tool
  ln -sf /usr/bin/kmod /usr/bin/$tool
done
