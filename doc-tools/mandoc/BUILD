cat <<EOF > configure.local
PREFIX=/usr
SBINDIR=/usr/bin
MANDIR=/usr/share/man

CFLAGS="${CFLAGS} ${CPPFLAGS}"
LDFLAGS="${LDFLAGS}"

# conflicts with doc-tools/groff
BINM_SOELIM=msoelim
MANM_ROFF=mandoc_roff

# conflicts with docs/man-pages
MANM_MAN=mandoc_man

# conflicts with system man (we should consider switching to mandoc instead of man)
BINM_MAN=mman
BINM_APROPOS=mapropos
BINM_WHATIS=mwhatis
BINM_MAKEWHATIS=mmakewhatis
MANM_MDOC=mandoc_mdoc
MANM_EQN=mandoc_eqn
MANM_TBL=mandoc_tbl
MANM_MANCONF=mman.conf
EOF

default_build
