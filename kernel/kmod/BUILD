OPTS+=" --with-zlib \
        --with-xz \
        --with-openssl"

./configure --prefix=/usr     \
            --libdir=/usr/lib \
            --datarootdir=/usr/share \
            --includedir=/usr/include \
            $OPTS  &&

default_make &&

install -dm755 /{etc,usr/lib}/{depmod,modprobe}.d &&

# add symlinks to kmod
ln -sf /usr/bin/kmod "/usr/bin/lsmod"  &&
ln -sf /usr/bin/kmod "/usr/bin/modinfo"  &&
for tool in {ins,rm,dep}mod modprobe; do
  ln -sf /usr/bin/kmod "/usr/sbin/$tool"
done
