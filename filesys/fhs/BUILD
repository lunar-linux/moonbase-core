prepare_install &&

# / Requirements
mkdir -p ${DESTDIR}/{bin,boot,dev,etc,lib,media,mnt,opt,sbin,srv,tmp,usr,var} &&

# / Specific Options
mkdir -p ${DESTDIR}/{home,root} &&

# /etc Requirements
mkdir -p ${DESTDIR}/etc/opt &&

# /etc Specific Options
ln -sf /proc/self/mounts ${DESTDIR}/etc/mtab &&

# /lib Specific Options
mkdir -p ${DESTDIR}/lib/modules &&

# /usr Requirements
mkdir -p ${DESTDIR}/usr/{bin,include,lib,local,sbin,share} &&

# /usr Specific Options
mkdir -p ${DESTDIR}/usr/{games,src} &&

# /usr/local Requirements
mkdir -p ${DESTDIR}/usr/local/{bin,etc,games,include,lib,man,sbin,share,src} &&

# /usr/share Requirements
mkdir -p ${DESTDIR}/usr/share/{man,misc} &&

# /usr/share Specific Options
mkdir -p ${DESTDIR}/usr/share/games &&

# /var Requirements
mkdir -p ${DESTDIR}/var/{cache,lib,local,log,opt,spool,tmp} &&
# /var Systemd addition
ln -sfT ../run ${DESTDIR}/var/run &&
ln -sfT ../run/lock ${DESTDIR}/var/lock &&

# /var Specific Options
mkdir -p ${DESTDIR}/var/games &&

# Linux addition
mkdir -p ${DESTDIR}/{proc,sys} &&

# / Systemd addition
mkdir -p ${DESTDIR}/run/lock
