make &&
prepare_install &&

install -d -m755 /{etc/{ca-certificates/update.d,ssl/certs},usr/share/ca-certificates} &&
install -D -m644 sbin/update-ca-certificates.8 /usr/share/man/man8/update-ca-certificates.8 &&

make install &&

(
  cd /usr/share/ca-certificates
  find . -name '*.crt' | sort | cut -b3-
) > /etc/ca-certificates.conf &&

# Remove a compromised cert, see https://emudhra.we-have-a-problem.com/
sed -i \
  -e 's|^mozilla/emSign_ECC_Root_CA_-_G3.crt|!&|' \
  -e 's|^mozilla/Comodo_AAA_Services_root.crt|!&|' \
  /etc/ca-certificates.conf &&

# Make CA bundle present in the most popular places.
mkdir -p /etc/pki/tls /usr/share/ssl &&
ln -sf /etc/ssl/certs /etc/pki/tls/certs &&
ln -sf /etc/ssl/certs /usr/share/ssl/certs &&
ln -sf /etc/ssl/certs/ca-{certificates,bundle}.crt &&
/usr/sbin/update-ca-certificates --fresh &> /dev/null
