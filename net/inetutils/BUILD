(

  OPTS+=" --without-wrap       \
          --disable-servers    \
          --disable-ifconfig   \
          --disable-tftp       \
          --disable-tftpd      \
          --disable-logger     \
          --disable-ftp        \
          --disable-whois      \
          --disable-rpath      \
          --disable-rexec      \
          --disable-rexecd     \
          --disable-ping       \
          --disable-ping6      \
          --disable-inetd      \
          --disable-syslogd    \
          --disable-traceroute \
          --disable-uucpd      \
          --enable-talk        \
          --enable-hostname    \
          --enable-rsh         \
          --enable-ftp         \
          --enable-telnet      \
          --enable-rcp"        &&

  # Fixes an incompatibility with glibc-2.16
  sedit '/gets is a/d' lib/stdio.in.h &&

  default_build

) > $C_FIFO 2>&1
