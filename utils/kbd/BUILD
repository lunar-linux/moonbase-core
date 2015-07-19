OPTS+=" --datadir=/usr/share/kbd --mandir=/usr/share/man"

# rename keymap files with the same names
# this is needed because when only name of keymap is specified
# loadkeys loads the first keymap it can find, which is bad
# this should be removed when upstream adopts the change
mv data/keymaps/i386/qwertz/cz{,-qwertz}.map &&
mv data/keymaps/i386/olpc/es{,-olpc}.map &&
mv data/keymaps/i386/olpc/pt{,-olpc}.map &&
mv data/keymaps/i386/dvorak/no{,-dvorak}.map &&
mv data/keymaps/i386/fgGIod/trf{,-fgGIod}.map &&

default_config &&
make KEYCODES_PROGS=yes RESIZECONS_PROGS=yes &&

prepare_install  &&
make KEYCODES_PROGS=yes RESIZECONS_PROGS=yes install
