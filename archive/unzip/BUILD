patch -p1 -F3 -i $SCRIPT_DIRECTORY/cve-2022-0529-and-cve-2022-0530.patch &&

./configure &&

# DEFINES, make, and install args from Debian
DEFINES='-DACORN_FTYPE_NFS -DWILD_STOP_AT_DIR -DLARGE_FILE_SUPPORT \
         -DUNICODE_SUPPORT -DUNICODE_WCHAR -DUTF8_MAYBE_NATIVE -DNO_LCHMOD \
         -DDATE_FORMAT=DF_YMD -DUSE_BZIP2 -DNOMEMCPY -DNO_WORKING_ISPRINT'

make -f unix/Makefile prefix=/usr D_USE_BZ2=-DUSE_BZIP2 L_BZ2=-lbz2 \
LF2="$LDFLAGS" CF="$CFLAGS $CPPFLAGS -I. $DEFINES" unzips

prepare_install &&
make -f unix/Makefile prefix=/usr install
