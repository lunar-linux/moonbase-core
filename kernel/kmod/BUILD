OPTS+=" --with-zlib \
        --with-xz \
        --with-openssl"

./configure --prefix=     \
            --libdir=/lib \
            --datarootdir=/usr/share \
            --includedir=/usr/include \
            $OPTS  &&

default_make &&

install -dm755 /{etc,usr/lib}/{depmod,modprobe}.d &&

# add symlinks to kmod
ln -sf /bin/kmod "/bin/lsmod"  &&
for tool in {ins,rm,dep}mod mod{info,probe}; do
  ln -sf /bin/kmod "/sbin/$tool"
done
