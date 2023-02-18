OPTS+="-Dstrip=true \
      -Dbuild-kill=disabled"

default_meson_build &&
prepare_install &&
chmod 700 /usr/bin/wall &&
chmod 4711 /usr/bin/{newgrp,ch{sh,fn}} &&
if [ -f /usr/lib/systemd/system/uidd.socket ]
then
    sedit '/ListenStream/ aRuntimeDirectory=uuidd' /usr/lib/systemd/system/uuidd.socket
fi &&
install -g0 -o0 -m755 $SCRIPT_DIRECTORY/make-issue /usr/bin/make-issue &&
install -Dm644 $SCRIPT_DIRECTORY/60-rfkill.rules /usr/lib/udev/rules.d/60-rfkill.rules &&
ln -sf /usr/bin/last /usr/bin/lastb
