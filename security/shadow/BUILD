set_login_opts() {
  local option=$1 value=$2
  if [[ "$value" == "empty" ]]; then
    sed -r -i "/^${option}/s;.*;${option};" etc/login.defs
  elif [[ -z $value ]]; then
    # comment
    sed -r -i "/^#?${option}/s;.*;#&;" etc/login.defs
  else
    # uncomment and set value
    sed -r -i "/^#?${option}/s;.*;${option} ${value};" etc/login.defs
  fi
}

# Keep shadow from installing it's own pam.d files
sedit '/^SUBDIRS/ n; s/etc//' Makefile.in Makefile.am &&

./configure --prefix=/usr \
            --bindir=/usr/bin \
            --sbindir=/usr/bin \
            --with-sha-crypt \
            --with-libcrack \
            --without-selinux \
            --without-skey \
            --without-group-name-max-length \
            --disable-static \
            $OPTS &&
make &&
mkdir -p $SOURCE_DIRECTORY/__shadowdest &&
make DESTDIR=$SOURCE_DIRECTORY/__shadowdest/ suidperms=4711 install &&

# remove the installed chfn, chsh, login, nologin, su, vigr and vipw apps
# util-linux install these apps in Lunar
cp $SOURCE_DIRECTORY/__shadowdest/usr/bin/login /tmp/ &&
rm $SOURCE_DIRECTORY/__shadowdest/usr/bin/{login,su,chfn,chsh,nologin} &&
rm $SOURCE_DIRECTORY/__shadowdest/usr/sbin/{vigr,vipw,logoutd} &&

# Move stuff to bin
mv $SOURCE_DIRECTORY/__shadowdest/usr/sbin/* $SOURCE_DIRECTORY/__shadowdest/usr/bin/ &&
mv $SOURCE_DIRECTORY/__shadowdest/usr/bin/{newgrp,sg} &&
rm -rf $SOURCE_DIRECTORY/__shadowdest/usr/sbin &&

# ...and their many man pages
find $SOURCE_DIRECTORY/__shadowdest/usr/share/man \
     '(' -name 'chsh.1'    -o \
         -name 'chfn.1'    -o \
         -name 'login.1'   -o \
         -name 'su.1'      -o \
         -name 'logoutd.8' -o \
         -name 'nologin.8' -o \
         -name 'vigr.8'    -o \
         -name 'vipw.8'   ')' \
      -delete &&

# Now install the cleaned up files from DESTDIR
prepare_install &&
cp -rfp --remove-destination $SOURCE_DIRECTORY/__shadowdest/* / &&

# We only need these files without PAM
if ! module_installed Linux-PAM; then
  set_login_opts CRACKLIB_DICTPATH /lib/cracklib/pw_dict
  set_login_opts ENCRYPT_METHOD SHA512
  set_login_opts LOGON_RETRIES 3

  [ -e /etc/limits ]       || install -m 0644 etc/limits       /etc/
  [ -e /etc/login.access ] || install -m 0644 etc/login.access /etc/
  [ -e /etc/login.defs ]   || install -m 0644 etc/login.defs   /etc/
else
  # Disable pam incompatible options
  for lopt in FAILLOG_ENAB LASTLOG_ENAB MAIL_CHECK_ENAB \
              OBSCURE_CHECKS_ENAB PORTTIME_CHECKS_ENAB QUOTAS_ENAB \
              FTMP_FILE NOLOGINS_FILE ENV_HZ PASS_MIN_LEN \
              SU_WHEEL_ONLY CRACKLIB_DICTPATH PASS_CHANGE_TRIES \
              PASS_ALWAYS_WARN CHFN_AUTH ENVIRON_FILE; do
    set_login_opts $lopt
  done
  set_login_opts MOTD_FILE empty
  set_login_opts ENCRYPT_METHOD SHA512

  [ -e /etc/login.defs ] || install -m 0644 etc/login.defs /etc/login.defs
fi &&

[ -e /etc/securetty ] || install -m 0644 $SCRIPT_DIRECTORY/securetty /etc/ &&
install $SCRIPT_DIRECTORY/adduser /usr/bin/ &&
install $SCRIPT_DIRECTORY/deluser /usr/bin/
