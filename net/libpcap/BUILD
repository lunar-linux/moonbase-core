
  patch_it $SOURCE2 1 &&

  if module_installed bluez-5 ; then
    OPTS+=" --enable-bluetooth"
  fi &&

  sedit "s/all: libpcap.a shared pcap-config/all: shared pcap-config/g" Makefile.in &&
  sedit "s/install: install-shared install-archive pcap-config/install: install-shared pcap-config/g" Makefile.in &&


  default_build
