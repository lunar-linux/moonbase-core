OPTS+=" --runstatedir=/run \
        --privsepuser=dhcpcd \
        --dbdir=/var/lib/dhcpcd"

default_build &&

# Set Options in /etc/dhcpcd.conf
# Disable ip4vall
echo noipv4ll >> /etc/dhcpcd.conf
