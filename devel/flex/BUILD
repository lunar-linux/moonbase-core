./configure --build=$BUILD \
            --prefix=/usr  \
            $OPTS         &&

sedit 's/ln -s/ln -sf/' Makefile &&
default_make &&

ln -sf flex /usr/bin/lex
