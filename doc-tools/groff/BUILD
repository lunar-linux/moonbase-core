if in_depends $MODULE libXaw; then
  OPTS+="-with-appresdir=/usr/share/X11/app-defaults"
fi

default_build &&

cd /usr/bin &&

if [ ! -e geqn ]; then
  ln -sf eqn geqn
fi &&

if [ ! -e gtbl ]; then
  ln -sf tbl gtbl
fi &&

if [ ! -e zsoelim ]; then
  ln -sf soelim zsoelim
fi

# TERMCAP variables not followed
# TODO: everyone is doing this - find out why upstream does not...
cat "$SCRIPT_DIRECTORY"/site.tmac >> /usr/share/groff/site-tmac/man.local
cat "$SCRIPT_DIRECTORY"/site.tmac >> /usr/share/groff/site-tmac/mdoc.local
