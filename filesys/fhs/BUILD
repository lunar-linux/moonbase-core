prepare_install &&

# / Requirements
mkdir -p /{boot,dev,etc,media,mnt,opt,srv,tmp,usr,var,run} &&

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

# https://www.freedesktop.org/wiki/Software/systemd/TheCaseForTheUsrMerge/
ln -sfT /usr/bin /bin &&
ln -sfT /usr/lib /lib &&
ln -sfT /usr/sbin /sbin &&

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
mkdir -p /run/lock
