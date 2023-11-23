pkgname=go2rtc-cameras
pkgver=0.0.1
pkgrel=1
arch=('any')
depends=(
  'ffmpeg'
  'jq'
)
source=(
  "cameras.json"
)
sha256sums=(
  'SKIP'
)

prepare() {
  cd "$srcdir"
  go2rtc_base_url=$(jq -r '.go2rtc' cameras.json)
  camera_stream_suffix=$(jq -r '.suffix' cameras.json)
  jq -r '.cameras | to_entries[] | .key + " " + .value' cameras.json | while read -r key value; do
    cat >"$key.desktop" <<EOF
[Desktop Entry]
Name=$value
Comment=Show $value camera stream
Exec=ffplay -fflags nobuffer -flags low_delay -rtsp_transport tcp "rtsp://$go2rtc_base_url/$key$camera_stream_suffix"
Type=Application
Categories=Media;
EOF
  done
}

package() {
  cd "$srcdir"
  for f in *.desktop; do
    install -Dm644 "$f" "$pkgdir/usr/share/applications/$f"
  done
}
