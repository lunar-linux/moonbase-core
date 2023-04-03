if [[ "$COLOR" == "y" ]]; then
  OPTS+=" --enable-color"
fi

if [[ "$NANORC" == "y" ]]; then
  OPTS+=" --enable-nanorc"
fi

if [[ "$MULTI" == "y" ]]; then
  OPTS+=" --enable-multibuffer"
fi

default_build &&

if [[ "$NANORC" == "y" && ! -f "/etc/nanorc" ]]; then
  install -m 0644 $SCRIPT_DIRECTORY/nanorc /etc/
fi
