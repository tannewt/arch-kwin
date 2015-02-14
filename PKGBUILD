# Maintainer: Andrea Scarpino <andrea@archlinux.org>

pkgname=kwin
pkgver=5.2.0.1
_dir=5.2.0
pkgrel=3
pkgdesc='KDE Window manager'
arch=('i686' 'x86_64')
url='https://projects.kde.org/projects/kde/workspace/kwin'
license=('LGPL')
depends=('qt5-multimedia' 'plasma-framework' 'knewstuff' 'libxcursor' 'kinit'
         'hicolor-icon-theme' 'libepoxy' 'kwayland' 'libinput' 'kdecoration')
makedepends=('extra-cmake-modules' 'qt5-tools' 'kdoctools')
groups=('plasma')
install=${pkgname}.install
conflicts=('kdebase-workspace')
source=("http://download.kde.org/stable/plasma/${_dir}/${pkgname}-${pkgver}.tar.xz"
        'kdebug-341971.patch'
        'libinput.0.8.0.patch')
md5sums=('47b6ce31b45450fa702098c9f3f5ac95'
         '037db2eab5f9e07c74122f1a5fd4fe31'
         '0ccc6b0113e37bd994c65ffb6a4518ff')

prepare() {
  mkdir build

  cd ${pkgname}-${pkgver}
  patch -p1 -i "${srcdir}"/kdebug-341971.patch
  
  #https://bugs.kde.org/show_bug.cgi?id=342893
  patch -Np1 -i "${srcdir}"/libinput.0.8.0.patch
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
