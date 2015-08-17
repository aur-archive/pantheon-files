# Maintainer: Maxime Gauduin <alucryd@archlinux.org>

pkgname=pantheon-files
pkgver=0.1.6
pkgrel=1
pkgdesc='The Pantheon File Manager'
arch=('i686' 'x86_64')
url="https://launchpad.net/${pkgname}"
license=('GPL3')
depends=('gconf' 'desktop-file-utils' 'granite' 'libgee06' 'libnotify' 'libunity')
makedepends=('cmake' 'gnome-common' 'sqlite3' 'vala')
optdepends=('contractor-bzr: Various context menu entries'
            'pantheon-files-plugin-dropbox-bzr: Dropbox integration'
            'tumbler: Thumbnails generation')
conflicts=('marlin-bin' 'marlin-bzr')
install="${pkgname}.install"
source=("${url}/${pkgver:0:4}x/${pkgver}/+download/${pkgname}-${pkgver}.tgz")
sha256sums=('2ff9d44d69a496d2c4e072a535c0289ee590f9870d9f3976eb0dedda8db19cf6')

build() {
  cd ${pkgname}-${pkgver}

  if [[ -d build ]]; then
    rm -rf build
  fi
  mkdir build && cd build

  cmake .. -DCMAKE_INSTALL_PREFIX='/usr' -DGSETTINGS_COMPILE='OFF'
  make
}

package() {
  cd ${pkgname}-${pkgver}/build

  make DESTDIR="${pkgdir}" install
}

# vim: ts=2 sw=2 et:
