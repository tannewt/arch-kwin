# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Contributor: Andrea Scarpino <andrea@archlinux.org>

pkgname=kwin
pkgver=5.6.3
pkgrel=1
pkgdesc='KDE Window manager'
arch=('i686' 'x86_64')
url='https://www.kde.org/workspaces/plasmadesktop/'
license=('LGPL')
depends=('qt5-multimedia' 'kscreenlocker' 'knewstuff' 'xcb-util-cursor' 'hicolor-icon-theme' 'kdecoration' 'kinit' 'plasma-framework' 'kcmutils')
makedepends=('extra-cmake-modules' 'qt5-tools' 'kdoctools' 'libinput' 'python')
optdepends=('libinput: for kwin-wayland')
groups=('plasma')
install=${pkgname}.install
conflicts=('kdebase-workspace')
source=("http://download.kde.org/stable/plasma/${pkgver}/${pkgname}-${pkgver}.tar.xz")
md5sums=('c007cd5a6ecf2611a415062259f335d0')

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../${pkgname}-${pkgver} \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DKDE_INSTALL_LIBDIR=lib \
    -DKDE_INSTALL_LIBEXECDIR=lib \
    -DKDE_INSTALL_USE_QT_SYS_PATHS=ON \
    -DBUILD_TESTING=OFF
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}
