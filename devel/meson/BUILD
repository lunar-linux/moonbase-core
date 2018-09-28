prepare_install &&

python3 setup.py install --optimize=1 --root=${DESTDIR:-/} &&

for _f in data/syntax-highlighting/vim/*/*; do
   mkdir -p $DESTDIR/usr/share/vim/vimfiles/
   install -Dt $DESTDIR/usr/share/vim/vimfiles/$(basename "$(dirname "$_f")") -m644 $_f
done
