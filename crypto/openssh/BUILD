# don't allow root login by default
sedit 's/#PermitRootLogin yes/PermitRootLogin no/' sshd_config &&

add_priv_user sshd:sshd &&

OPTS=$OPTS" --sysconfdir=/etc/ssh --with-md5-passwords" &&
default_build  &&

# create /var/empty
mkdir -p /var/empty &&
chown root:sys /var/empty &&
chmod 755 /var/empty &&

# install ssh-copy-id script and man page
install -Dm755 {contrib,/usr/bin}/ssh-copy-id &&
install -Dm644 {contrib,/usr/share/man/man1}/ssh-copy-id.1
