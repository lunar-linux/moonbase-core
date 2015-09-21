./autogen.sh &&

if ! in_depends $MODULE asciidoc || ! in_depends $MODULE xmlto; then
  OPTS+=" --disable-documentation"
fi &&

OPTS+=" --bindir=/usr/bin" &&

default_build &&

# remove the static lib
rm /usr/lib/libbtrfs.a

