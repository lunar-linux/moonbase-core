CFLAGS="$CFLAGS -I$SOURCE_DIRECTORY/include $(pkg-config libnl-genl-3.0 --cflags)"

default_build &&

# backwards compatibility, programs often look for net/bpf.h
mkdir -p /usr/include/net &&

cd /usr/include/net &&
ln -sf ../pcap-bpf.h bpf.h
