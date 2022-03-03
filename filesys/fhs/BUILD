prepare_install &&

# / Requirements
mkdir -p /{bin,boot,dev,etc,lib,media,mnt,opt,sbin,srv,tmp,usr,var} &&

# / Specific Options
mkdir -p /{home,root} &&

# /etc Requirements
mkdir -p /etc/opt &&

# /etc Specific Options
ln -sf /proc/self/mounts /etc/mtab &&

# /lib Specific Options
mkdir -p /lib/modules &&

# /usr Requirements
mkdir -p /usr/{bin,include,lib,local,sbin,share} &&

# /usr Specific Options
mkdir -p /usr/{games,src} &&

# /usr/local Requirements
mkdir -p /usr/local/{bin,etc,games,include,lib,man,sbin,share,src} &&

# /usr/share Requirements
mkdir -p /usr/share/{man,misc} &&

# /usr/share Specific Options
mkdir -p /usr/share/games &&

# /var Requirements
mkdir -p /var/{cache,lib,local,log,opt,spool,tmp} &&
# /var Systemd addition
ln -sfT ../run /var/run &&
ln -sfT ../run/lock /var/lock &&

# /var Specific Options
mkdir -p /var/games &&

# Linux addition
mkdir -p /{proc,sys} &&

# / Systemd addition
mkdir -p /run/lock &&

# ld.so.conf and ld.so.conf.d
mkdir -p /etc/ld.so.conf.d &&

if [ ! -e "/etc/ld.so.conf" ]; then
  install -Dm644 $SCRIPT_DIRECTORY/templates/etc/ld.so.conf /etc/ld.so.conf
elif ! grep -q '^include /etc/ld\.so\.conf\.d/\*\.conf' /etc/ld.so.conf; then
  # Migration code
  echo "include /etc/ld.so.conf.d/*.conf" >> /etc/ld.so.conf
fi
