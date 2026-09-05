OPTS+=" --bindir=/usr/bin"

default_build &&

# Some considerations for hardcoded paths in non-usr-merged systems
if [[ ! -L /bin ]]; then
  for program in gunzip gzexe gzip uncompress zcat zcmp zdiff \
    zegrep zfgrep zforce zgrep zless zmore znew; do
      ln -sfv /usr/bin/$program /bin/
  done
fi
