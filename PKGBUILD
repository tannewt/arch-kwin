# Maintainer: Andrea Scarpino <andrea@archlinux.org>

pkgname=kwin
pkgver=5.1.2
pkgrel=1
pkgdesc='KDE Window manager'
arch=('i686' 'x86_64')
url='https://projects.kde.org/projects/kde/workspace/kwin'
license=('LGPL')
depends=('qt5-multimedia' 'plasma-framework' 'knewstuff' 'libxcursor' 'kinit'
         'hicolor-icon-theme' 'libepoxy' 'kwayland')
makedepends=('extra-cmake-modules' 'qt5-tools' 'kdoctools')
groups=('plasma-next')
install=${pkgname}.install
conflicts=('kdebase-workspace')
source=("http://download.kde.org/stable/plasma/${pkgver}/${pkgname}-${pkgver}.tar.xz")
md5sums=('feb97cc6591e2526406d988a8fcf2f20')

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../${pkgname}-${pkgver} \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DLIB_INSTALL_DIR=lib \
    -DLIBEXEC_INSTALL_DIR=lib \
    -DKDE_INSTALL_USE_QT_SYS_PATHS=ON \
    -DQML_INSTALL_DIR=lib/qt/qml \
    -DBUILD_TESTING=OFF
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}
