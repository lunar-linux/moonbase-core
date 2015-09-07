set_login_opts() {
  local option=$1 value=$2
  if [[ -z $value ]]; then
    # comment
    sed -r -i "/^#?${option}/s;.*;#&;" etc/login.defs
  else
    # uncomment and set value
    sed -r -i "/^#?${option}/s;.*;${option} ${value};" etc/login.defs
  fi
}

# Keep shadow from installing it's own pam.d files
sedit '/^SUBDIRS/ n; s/etc//' Makefile.in Makefile.am &&

./configure --with-sha-crypt \
            --with-libcrack \
            --without-selinux \
            --without-skey \
            --without-group-name-max-length \
            --disable-static \
            $OPTS &&

make &&
prepare_install &&
make suidperms=4711 install &&

# We only need these files without PAM
if ! module_installed Linux-PAM; then
  set_login_opts CRACKLIB_DICTPATH /lib/cracklib/pw_dict
  set_login_opts ENCRYPT_METHOD SHA512
  set_login_opts LOGON_RETRIES 3

  [ -e /etc/limits ]       || install -m 0644 etc/limits       /etc/
  [ -e /etc/login.access ] || install -m 0644 etc/login.access /etc/
  [ -e /etc/login.defs ]   || install -m 0644 etc/login.defs  /etc/
else
  # Disable pam incompatible options
  for lopt in FAILLOG_ENAB LASTLOG_ENAB MAIL_CHECK_ENAB \
              OBSCURE_CHECKS_ENAB PORTTIME_CHECKS_ENAB QUOTAS_ENAB \
              MOTD_FILE FTMP_FILE NOLOGINS_FILE ENV_HZ PASS_MIN_LEN \
              SU_WHEEL_ONLY CRACKLIB_DICTPATH PASS_CHANGE_TRIES \
              PASS_ALWAYS_WARN CHFN_AUTH ENVIRON_FILE; do
    set_login_opts $lopt
  done

  set_login_opts ENCRYPT_METHOD SHA512

  [ -e /etc/login.defs ] || install -m 0644 etc/login.defs /etc/login.defs
fi &&

[ -e /etc/securetty  ] || install -m 0644 $SCRIPT_DIRECTORY/securetty /etc/ &&
install $SCRIPT_DIRECTORY/adduser /usr/sbin/ &&
install $SCRIPT_DIRECTORY/deluser /usr/sbin/

# remove the installed chfn, chsh, login, su, nologin, vigr and vipw apps
# util-linux install these apps in Lunar
rm /usr/bin/{chfn,chsh,login,su} &&
rm /usr/sbin/{vigr,vipw} &&
rm /sbin/nologin &&

# ...and their many man pages
find /usr/share/man \
     '(' -name 'chsh.1'    -o \
         -name 'chfn.1'    -o \
         -name 'su.1'      -o \
         -name 'logoutd.8' -o \
         -name 'login.1'   -o \
         -name 'nologin.8' -o \
         -name 'vipw.8'    -o \
         -name 'vigr.8'    -o \
         -name 'newgrp.1' ')' \
      -delete &&

rm -fR /usr/share/man/{fi,id,zh_TW}/man1 \
       /usr/share/man/{fi,ko/man8}
