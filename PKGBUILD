# Maintainer: Andrea Scarpino <andrea@archlinux.org>

pkgname=kwin
pkgver=5.0.1
pkgrel=1
pkgdesc='KDE Window manager'
arch=('i686' 'x86_64')
url='https://projects.kde.org/projects/kde/workspace/kwin'
license=('LGPL')
depends=('qt5-multimedia' 'plasma-framework' 'kcmutils' 'knewstuff' 'libxcursor' 'kinit')
makedepends=('extra-cmake-modules' 'qt5-tools' 'kdoctools')
groups=('plasma-next')
install=${pkgname}.install
source=("http://download.kde.org/stable/plasma/${pkgver}/${pkgname}-${pkgver}.tar.xz")
md5sums=('b897099c71ba90fc909fa18d98255592')

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../${pkgname}-${pkgver} \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DLIB_INSTALL_DIR=lib \
    -DQT_PLUGIN_INSTALL_DIR=lib/qt/plugins \
    -DQML_INSTALL_DIR=lib/qt/qml \
    -DBUILD_TESTING=OFF \
    -DSYSCONF_INSTALL_DIR=/etc
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}
