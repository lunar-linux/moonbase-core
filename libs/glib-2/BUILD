(

  # Do not remove --enable-debug=minimum, it will break some common
  # API functions if debug is entirely disabled
  export OPTS+=" --disable-static --enable-shared --enable-debug=minimum --disable-fam --with-pcre=system"  &&

  # Disable docs (require Python and gdbus-codegen), we can enable
  # this later if necessary by introducing a glib-2-docs module
  sedit "s;^\(.*\SUBDIRS .*\=.*\)docs\(.*\)$;\1\2;" Makefile.in
  sedit "s;^\(.*\SUBDIRS .*\=.*\)docs\(.*\)$;\1\2;" Makefile.am

  # Don't build tests
  for i in $(find . -name Makefile.in -o -name Makefile.am); do
    sedit "s;^\(.*\SUBDIRS .*\=.*\)tests\(.*\)$;\1\2;" $i
  done

  # This patch splits out gdbus-codegen which is a separate module now
  patch_it $SOURCE2 1 &&

  sedit "s;AM_PROG_CC_STDC;;" configure.ac
#  AT_M4DIR=. autoreconf &&

  ./autogen.sh &&
  default_build

) > $C_FIFO 2>&1
