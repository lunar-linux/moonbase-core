# Before starting, see if any previous version of make exists and
# if it works correctly.  Basically this should work even if
# you've made a complete mess of your system and make no longer
# functions.
#
# Also deal with the (quite unusual) circumstance of guile being
# requested, but no longer working for whatever reason.  Someone
# reported it breaking upon upgrade of libffi, for example.

/usr/bin/make > /dev/null 2>& 1

if [[ $? -eq 127 ]]  # this means make's gone missing or can't load
then
    case "$OPTS" in
        *with-guile*)
            /usr/bin/guile > /dev/null 2>&1
            if [[ $? -eq 127 ]]  # and this means guile's broken (or missing)
            then
                # even though user asked for guile, don't use it this time round
                OPTS=" --disable-dependency-tracking --without-guile "
            fi
        ;;

        *)
            OPTS+=" --disable-dependency-tracking "
        ;;
    esac
fi

default_config &&

if ! make ${MAKES:-j${MAKES}}
then
  ./build.sh &&
  prepare_install &&
  ./make install
else
  prepare_install &&
  make install
fi
