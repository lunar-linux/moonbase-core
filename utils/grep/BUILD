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
default_build &&

# NOTE: current fgrep causes atlas build to fail. So far its the only module
# I've encountered. The issue is with this lin in fgrep;
# echo "$cmd: warning: $cmd is obsolescent; using grep -F" >&2
# So we'll just comment that out.
sed -i 's/^echo/#echo/' /usr/bin/fgrep
