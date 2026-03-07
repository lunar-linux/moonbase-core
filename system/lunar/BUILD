_ARCH=$(arch)

default_build &&

if [[ "$_ARCH" == "x86_64" ]]; then
  unpack $SOURCE2 &&
  install -Dm755 llint-v$VERSION-linux-amd64/llint-linux-amd64 /usr/bin/llint
else
  unpack $SOURCE3 &&
  install -Dm755 llint-v$VERSION-linux-i686/llint-linux-i686 /usr/bin/llint
fi

