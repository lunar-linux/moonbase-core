./configure &&
make linux_shlib &&
make linux &&

prepare_install &&

make install &&

cp -af libunzip.s* ${DESTDIR:-}/usr/lib &&
gather_docs BUGS WHERE ToDo
