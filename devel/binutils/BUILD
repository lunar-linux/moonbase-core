# Following the build procedure used by the LFS folks
mkdir -p build-binutils &&
cd build-binutils &&

../configure --prefix=/usr    \
             --disable-werror \
             --enable-shared  \
             --enable-gold    \
             $OPTS           &&

make tooldir=/usr &&
prepare_install &&
make tooldir=/usr install &&
make tooldir=/usr install-info &&
mkdir -p $DOCUMENT_DIRECTORY/binutils &&
cp -p ../binutils/NEWS ../binutils/ChangeLog $DOCUMENT_DIRECTORY/binutils &&

# For some reason installwatch fail to pick up the ld hardlink, touching it solves that issue
if [ -e /usr/bin/ld ]; then
  touch /usr/bin/ld
fi

# Remove unwanted files
rm /usr/share/man/man1/{dlltool,nlmconv,windres,windmc}*
