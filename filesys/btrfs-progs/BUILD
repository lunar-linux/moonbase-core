./autogen.sh &&

if ! in_depends $MODULE asciidoc || ! in_depends $MODULE xmlto; then
  OPTS+=" --disable-documentation"
fi &&

./configure prefix=/usr \
            --bindir=/sbin \
            $OPTS &&

default_make
