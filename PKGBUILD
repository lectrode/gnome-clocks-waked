# Maintainer: lectrode (electrodexsnet@gmail.com)
# Contributor: Jan Alexander Steffens (heftig) <heftig@archlinux.org>

_pkgname=gnome-clocks
pkgname=${_pkgname}-mobile
pkgver=43.0
pkgrel=1
pkgdesc="Clocks applications for GNOME"
url="https://wiki.gnome.org/Apps/Clocks"
arch=(x86_64 aarch64)
license=(GPL)
provides=($_pkgname)
conflicts=($_pkgname)
depends=(gtk4 libgweather-4 gnome-desktop-4 geoclue geocode-glib-2 gsound
         libadwaita waked)
makedepends=(vala gobject-introspection yelp-tools git meson)
groups=(gnome)
options=(debug)
_commit=9877dfa0ca9fcc2fcf73fd6d96b57226380baf4a  # tags/43.0^0
source=("git+https://gitlab.gnome.org/GNOME/gnome-clocks.git#commit=$_commit"
        '0001-invoke-waked-when-an-alarm-changes.patch'
        '0002-Add-argument-to-start-initial-instance-in-the-backgr.patch'
        'gnome-clocks.desktop')
sha256sums=('SKIP'
            'SKIP'
            'SKIP'
            'SKIP')

pkgver() {
  cd $_pkgname
  git describe --tags | sed 's/[^-]*-g/r&/;s/-/+/g'
}

prepare() {
  cd $_pkgname

  local src
  for src in "${source[@]}"; do
    src="${src%%::*}"
    src="${src##*/}"
    [[ $src = *.patch ]] || continue
    echo "Applying patch $src..."
    patch -Np1 < "../$src"
  done
}

build() {
  arch-meson $_pkgname build
  meson compile -C build
}

check() {
  meson test -C build --print-errorlogs
}

package() {
  meson install -C build --destdir "$pkgdir"
  install -Dm644 "gnome-clocks.desktop" "${pkgdir}/etc/xdg/autostart/gnome-clocks.desktop"
}

# vim:set sw=2 sts=-1 et:
