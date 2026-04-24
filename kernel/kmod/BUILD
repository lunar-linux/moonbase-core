OPTS+=" --with-zlib \
        --with-xz \
        --with-openssl"

default_build &&

install -dm755 /{etc,usr/lib}/{depmod,modprobe}.d &&

# add symlinks to kmod
ln -sf /usr/bin/kmod "/usr/bin/lsmod"  &&
for tool in {ins,rm,dep}mod mod{info,probe}; do
  ln -sf /usr/bin/kmod "/usr/sbin/$tool"
done
