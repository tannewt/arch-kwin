# Maintainer: Andrea Scarpino <andrea@archlinux.org>

pkgname=kwin
pkgver=4.96.0
pkgrel=1
pkgdesc='KDE Window manager'
arch=('i686' 'x86_64')
url='https://projects.kde.org/projects/kde/workspace/kwin'
license=('LGPL')
depends=('qt5-multimedia' 'plasma-framework' 'kcmutils' 'knewstuff' 'libxcursor')
makedepends=('extra-cmake-modules' 'qt5-tools' 'kdoctools')
groups=('plasma-next')
source=("http://download.kde.org/unstable/plasma/${pkgver}/src/${pkgname}-${pkgver}.tar.xz")
md5sums=('49cad6bb303ef64b375a6eb6f187f3c9')

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../${pkgname}-${pkgver} \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/opt/kf5 \
    -DLIB_INSTALL_DIR=lib \
    -DBUILD_TESTING=OFF
#    -DSYSCONF_INSTALL_DIR=/etc
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}
