if [ "$USE_PERL" == "y" ]; then
  OPTS=$OPTS" --enable-perl-regexp"
else
  OPTS=$OPTS" --disable-perl-regexp"
fi &&

if [ "$USE_LARGEFILE" == "y" ]; then
  OPTS=$OPTS" --enable-largefile"
else
  OPTS=$OPTS" --disable-largefile"
fi &&

if [ "$USE_NLS" == "y" ]; then
  OPTS=$OPTS" --enable-nls"
else
  OPTS=$OPTS" --disable-nls"
fi &&

sedit "s/SYMLINK=\"ln -s\"/SYMLINK=\"ln -sf\"/" configure &&
default_build
