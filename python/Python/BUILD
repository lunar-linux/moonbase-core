OPTS+=" --enable-shared" &&

default_build &&

install -d /usr/lib/python${VERSION%.*} &&
install -m755 $SOURCE_DIRECTORY/Tools/i18n/msgfmt.py    \
              $SOURCE_DIRECTORY/Tools/i18n/pygettext.py \
              /usr/lib/python${VERSION%.*}             &&

# Docs
mv Misc/{cheatsheet,NEWS} . &&
chmod 644 cheatsheet NEWS README &&
gather_docs cheatsheet NEWS README
