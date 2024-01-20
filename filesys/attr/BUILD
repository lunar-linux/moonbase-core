# http://lists.gnu.org/archive/html/bug-coreutils/2019-03/msg00008.html
sed -i '/nfs/d' xattr.conf &&

export DEBUG=-DNDEBUG &&
export INSTALL_USER=root INSTALL_GROUP=root &&

OPTS+=" --disable-static" &&

default_build
