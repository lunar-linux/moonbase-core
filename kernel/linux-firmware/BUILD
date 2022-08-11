_DESTDIR=$SOURCE_DIRECTORY/__destdir

make DESTDIR="${_DESTDIR}" FIRMWAREDIR=/lib/firmware installcompress &&

if [[ "$FW_NFP" != "y" ]]; then
  rm -rf "$_DESTDIR/lib/firmware/netronome" &&
  rm -f "$SOURCE_DIRECTORY/LICENSE.Netronome"
fi &&

if [[ "$FW_MELLANOX" != "y" ]]; then
  rm -rf "$_DESTDIR/lib/firmware/mellanox"
fi &&

if [[ "$FW_MARVELL" != "y" ]]; then
  rm -rf "$_DESTDIR"/lib/firmware/{libertas,mwl8k,mwlwifi,mrvl} &&
  rm -f "$SOURCE_DIRECTORY"/LICENSE.{Marvell,NXP}
fi &&

if [[ "$FW_QCOM" != "y" ]]; then
  rm -rf "$_DESTDIR"/lib/firmware/{qcom,a300_*} &&
  rm -f "$SOURCE_DIRECTORY"/LICENSE.qcom
fi &&

if [[ "$FW_LIQUIDIO" != "y" ]]; then
  rm -rf "$_DESTDIR"/lib/firmware/liquidio &&
  rm -f "$SOURCE_DIRECTORY"/LICENSE.cavium_liquidio
fi &&

if [[ "$FW_QLOGIC" != "y" ]]; then
  rm -rf "$_DESTDIR"/lib/firmware/{qlogic,qed,ql2???_*,c{b,t,t2}fw-*} &&
  rm -f "$SOURCE_DIRECTORY"/LICENSE.{qla1280,qla2xxx}
fi &&

if [[ "$FW_BNX2X" != "y" ]]; then
  rm -rf "$_DESTDIR"/lib/firmware/bnx2x*
fi &&

prepare_install &&

cp -rf --remove-destination $_DESTDIR/* / &&

gather_docs GPL* LICEN* WHENCE
