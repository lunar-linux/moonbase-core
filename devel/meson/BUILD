default_python3_build &&

for _f in data/syntax-highlighting/vim/*/*; do
   install -Dt /usr/share/vim/vimfiles/$(basename "$(dirname "$_f")") -m644 $_f
done
