# Maintainer: BanHammer  <no@e.mail>

pkgname=google-antigravity
pkgver=1.11.3_6583016683339776
_pkgver=1.11.3-6583016683339776
pkgrel=1
pkgdesc="Google Antigravity is an agentic development platform, evolving the IDE into the agent-first era."
arch=('x86_64')
url="https://antigravity.google/"
license=('custom')
makedepends=()
depends=(libxkbfile gnupg gtk3 libsecret nss gcc-libs libnotify libxss glibc lsof shared-mime-info xdg-utils alsa-lib)
optdepends=('glib2: Needed for move to trash functionality'
            'libdbusmenu-glib: Needed for KDE global menu'
            'org.freedesktop.secrets: Needed for settings sync'
             # See https://github.com/MicrosoftDocs/live-share/issues/4650
            'icu69: Needed for live share' )
options=('!strip')
source=("https://edgedl.me.gvt1.com/edgedl/release2/j0qc3/antigravity/stable/$_pkgver/linux-x64/Antigravity.tar.gz")
sha256sums=('025da512f9799a7154e2cc75bc0908201382c1acf2e8378f9da235cb84a5615b')

package() {
  cd "$srcdir/Antigravity"

  install -d "$pkgdir/opt/antigravity"
  cp -a ./* "$pkgdir/opt/antigravity/"

  # Chromium sandbox permissions
  if [[ -f "$pkgdir/opt/antigravity/chrome-sandbox" ]]; then
    chmod 4755 "$pkgdir/opt/antigravity/chrome-sandbox"
  fi

  # Symlink binary (adjust if wrong)
  install -d "$pkgdir/usr/bin"
  ln -s /opt/antigravity/antigravity "$pkgdir/usr/bin/antigravity"

  # Icon
  install -Dm644 "$srcdir/Antigravity/resources/app/resources/linux/code.png" "$pkgdir/usr/share/pixmaps/antigravity.png"

  # Desktop entry
  install -d "$pkgdir/usr/share/applications"
  cat > "$pkgdir/usr/share/applications/antigravity.desktop" <<EOF
[Desktop Entry]
Type=Application
Name=Antigravity
Exec=antigravity
Icon=antigravity
Categories=Development;IDE;
StartupWMClass=Antigravity
EOF
}
