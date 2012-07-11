(

  # Do not remove --enable-debug=minimum, it will break some common
  # API functions if debug is entirely disabled
  export OPTS+=" --disable-static --enable-shared --enable-debug=minimum --disable-fam"  &&

  if [ "$DOCS" = "n" ] || ! in_depends $MODULE Python; then
    sedit "s;^\(.*\SUBDIRS .*\=.*\)docs\(.*\)$;\1\2;" Makefile.in
    sedit "s;^\(.*\SUBDIRS .*\=.*\)docs\(.*\)$;\1\2;" Makefile.am
  fi  &&

  # Don't build tests if we don't have python
  # Tests are required if docs are built
  if ! in_depends $MODULE Python && [ "$DOCS" = "n" ]; then
    for i in $(find . -name Makefile.in -o -name Makefile.am); do
      sedit "s;^\(.*\SUBDIRS .*\=.*\)tests\(.*\)$;\1\2;" $i
    done
  fi &&

  patch_it $SOURCE2 1 &&
  AT_M4DIR=. autoreconf && 
  default_build

) > $C_FIFO 2>&1
