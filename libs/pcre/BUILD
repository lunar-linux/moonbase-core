bad_flags ALL &&

OPTS+=" --enable-jit \
        --enable-utf8 \
        --enable-pcre16 \
        --enable-pcre32 \
        --enable-pcregrep-libz \
        --enable-pcregrep-libbz2 \
        --enable-unicode-properties \
        --disable-static" &&

default_config &&

sedit 's:ln -s:ln -sf:' Makefile &&

if [ -f /usr/lib/libpcre.so.0.0.1 ]; then
# preserve the old version to prevent the crash of grep
  make &&
  make install &&
# rebuild the new grep image
  lin grep
fi &&

# normal install of pcre
default_make
