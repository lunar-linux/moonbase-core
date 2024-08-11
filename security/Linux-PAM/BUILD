export SGML2LATEX=no
export SGML2TXT=no
export SGML2HTML=no
export SGML2PS=no
export PS2PDF=no

# Stop pam_env from installing /etc/environment
sedit "/^sysconf_DATA/d" modules/pam_env/Makefile.am  &&

aclocal &&
libtoolize -f &&
AT_M4DIR="m4" autoreconf -i &&

./configure  --libdir=/lib                            \
             --docdir=/usr/share/doc/Linux-PAM        \
             --disable-prelude                        \
             --disable-static                         \
             --disable-nis                            \
             --mandir=/usr/share/man                  \
             --enable-db=no                           \
             --disable-selinux                        \
             --disable-audit                          \
             --enable-isadir=../../lib/security       \
             --enable-nls                             \
             --disable-regenerate-docu                \
             $OPTS &&

sedit  "s/examples//"  Makefile           &&
sedit  "s/read yes//"  conf/install_conf  &&

make -C po update-gmo &&
make &&

prepare_install &&
make install &&

for i in auth acct passwd session; do
  ln -sf pam_unix.so /lib/security/pam_unix_${i}.so
done &&

# Makefile no longer setsuid on unix_chkpwd and pam_timestamp_check
chmod 4711 /sbin/unix_chkpwd &&
chmod 4711 /sbin/pam_timestamp_check &&

# Module documents are nice
if [ ! -d /usr/share/doc/Linux-PAM/txt ]; then
  mkdir -p /usr/share/doc/Linux-PAM/txt
fi &&
for i in $SOURCE_DIRECTORY/modules/pam_*/README; do
  cp -f ${i} /usr/share/doc/Linux-PAM/txt/README.$(echo ${i} | awk -F/ '{ print $(NF-1) }')
done &&

# More doc
gather_docs AUTHORS Copyright &&

( [ -f /etc/environment ] || touch /etc/environment ) &&
( [ -f /etc/security/limits.conf ] || install -m 0644 modules/pam_limits/limits.conf /etc/security/ )
