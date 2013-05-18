patch_it $SOURCE2 1 &&

# fixed in next version
# http://git.kernel.org/cgit/linux/kernel/git/shemminger/iproute2.git/commit/?id=824c843556a80cd3b4003d1e9e583cfdf632d0c0
sedit "s:sizeof(th\.hdr\[i\]):HDR_LINE_LENGTH:" misc/lnstat.c &&

if ! in_depends $MODULE db; then
  sedit 's/arpd//' misc/Makefile
fi &&

./configure &&
KERNEL_INCLUDE=/usr/include/ make &&
prepare_install &&
make install
