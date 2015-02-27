
# https://bugzilla.redhat.com/show_bug.cgi?id=1153753
  patch_it $SOURCE3 1 &&

# https://bugzilla.gnome.org/show_bug.cgi?id=738805 fix for CVE-2014-3660
  patch_it $SOURCE4 1 &&

  OPTS+=" --disable-static" &&

  patch_it $SOURCE2 1 &&
  default_build
