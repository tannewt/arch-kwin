# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Contributor: Andrea Scarpino <andrea@archlinux.org>

pkgname=kwin
pkgver=5.4.3
pkgrel=2
pkgdesc='KDE Window manager'
arch=('i686' 'x86_64')
url='https://projects.kde.org/projects/kde/workspace/kwin'
license=('LGPL')
depends=('qt5-multimedia' 'plasma-framework' 'knewstuff' 'xcb-util-cursor' 'kinit'
         'hicolor-icon-theme' 'kwayland' 'kdecoration')
makedepends=('extra-cmake-modules' 'qt5-tools' 'kdoctools')
groups=('plasma')
install=${pkgname}.install
conflicts=('kdebase-workspace')
source=("http://download.kde.org/stable/plasma/${pkgver}/${pkgname}-${pkgver}.tar.xz")
md5sums=('0ec5dcf4776b7ad9a0231c04f739039d')

prepare() {
  mkdir build
}

build() {
  cd build
  cmake ../${pkgname}-${pkgver} \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DLIB_INSTALL_DIR=lib \
    -DLIBEXEC_INSTALL_DIR=lib \
    -DKDE_INSTALL_USE_QT_SYS_PATHS=ON \
    -DBUILD_TESTING=OFF
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}
