# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Contributor: Andrea Scarpino <andrea@archlinux.org>

pkgname=kwin
pkgver=5.8.4
pkgrel=1
pkgdesc='KDE Window manager'
arch=('i686' 'x86_64')
url='https://www.kde.org/workspaces/plasmadesktop/'
license=('LGPL')
depends=('qt5-multimedia' 'kscreenlocker' 'knewstuff' 'xcb-util-cursor' 'hicolor-icon-theme'
         'plasma-framework' 'kcmutils' 'breeze')
makedepends=('extra-cmake-modules' 'qt5-tools' 'kdoctools' 'python')
optdepends=('qt5-virtualkeyboard: virtual keyboard support for kwin-wayland')
groups=('plasma')
conflicts=('kdebase-workspace')
source=("http://download.kde.org/stable/plasma/${pkgver}/${pkgname}-${pkgver}.tar.xz"{,.sig})
sha256sums=('d60d7ffece656fb693da54369034bca14b6c3f2c750454b7213c2ac1c4aff4fd'
            'SKIP')
validpgpkeys=('2D1D5B0588357787DE9EE225EC94D18F7F05997E'  # Jonathan Riddell
              '348C8651206633FD983A8FC4DEACEA00075E1D76'  # KDE Neon
              'D07BD8662C56CB291B316EB2F5675605C74E02CF') # David Edmundson

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../$pkgname-$pkgver \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DKDE_INSTALL_LIBDIR=lib \
    -DKDE_INSTALL_LIBEXECDIR=lib \
    -DBUILD_TESTING=OFF
  make
}

package() {
  cd build
  make DESTDIR="$pkgdir" install
}
