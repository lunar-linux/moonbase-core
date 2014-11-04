(

  cd wpa_supplicant  &&
  cp $SCRIPT_DIRECTORY/config ./.config  &&
  sedit "s/\/usr\/local/\/usr/g"  Makefile  &&
  sedit "s/dynamic_eap_methods//" Makefile  &&

  for option in \
      DNET_PCAP CTRL_IFACE \
      DRIVER_{HOSTAP,PRISM54,NL80211,NDISWRAPPER,ATMEL,WEXT,IPW,WIRED} \
      WIRELESS_EXTENSION IEEE8021X_EAPOL MSCHAPV2 \
      EAP_{MD5,TLS,PEAP,TTLS,GTC,OTP,SIM,AKA,PSK,LEAP}
  do
    echo "CONFIG_${option}=y" >> .config
  done  &&

  if [ "${OPTS/*--dbus-no*/n}" != "n" ]; then
     echo "CONFIG_CTRL_IFACE_DBUS_NEW=y" >> .config
  fi &&

  make  &&

  prepare_install  &&
  make install     &&

  if [ "${OPTS/*--dbus-no*/n}" != "n" ]; then
    install -m644 dbus/dbus-wpa_supplicant.conf /etc/dbus-1/system.d/
  fi  &&
  install -m644 wpa_supplicant.conf /etc/wpa_supplicant.conf.example  &&

  gather_docs developer.txt wpa_supplicant.conf

) > $C_FIFO 2>&1
