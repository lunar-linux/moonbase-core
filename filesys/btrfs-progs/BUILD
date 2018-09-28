./autogen.sh &&

if ! in_depends $MODULE asciidoc || ! in_depends $MODULE xmlto; then
  OPTS+=" --disable-documentation"
fi &&

default_build &&

# remove the static lib
rm $DESTDIR/usr/lib/libbtrfs.a &&

# install bash completion
install -Dm644 btrfs-completion $DESTDIR/usr/share/bash-completion/completions/btrfs
