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

# Always overwrite ld.so.conf with our version
install -Dm644 $SCRIPT_DIRECTORY/templates/etc/ld.so.conf /etc/ld.so.conf &&

# Migration code
if [ ! -e "/etc/nsswitch.conf" ] || [ "$(md5sum /etc/nsswitch.conf | cut -d' ' -f1)" == "3579b33b39600875ee113b4b63e895c5" ]; then
  install -Dm644 $SCRIPT_DIRECTORY/templates/etc/nsswitch.conf /etc/nsswitch.conf
fi
