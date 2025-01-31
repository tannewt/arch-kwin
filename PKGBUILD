# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Maintainer: Antonio Rojas <arojas@archlinux.org>
# Contributor: Andrea Scarpino <andrea@archlinux.org>

pkgname=kwin
pkgver=6.0.3.1
_dirver=$(echo $pkgver | cut -d. -f1-3)
pkgrel=5
pkgdesc='An easy to use, but flexible, composited Window Manager'
arch=(x86_64)
url='https://kde.org/plasma-desktop/'
license=(LGPL-2.0-or-later)
depends=(breeze
	gcc-libs
	glibc
	plasma-activities
	kauth
	kcmutils
	kcolorscheme
	kconfig
	kconfigwidgets
	kcoreaddons
	kcrash
	kdbusaddons
	kdeclarative
	kdecoration
	kglobalaccel
	kglobalacceld
	kguiaddons
	ki18n
	kidletime
	kirigami
	kitemmodels
	knewstuff
	knotifications
	kpackage
	kquickcharts
	kscreenlocker
	kservice
	ksvg
	kwayland
	kwidgetsaddons
	kwindowsystem
	kxmlgui
	lcms2
	libdisplay-info
	libdrm
	libepoxy
	libinput
	libpipewire
	libqaccessibilityclient-qt6
	libx11
	libxcb
	libxcvt
	libxi
	libxkbcommon
	libxkbcommon-x11
	mesa
	pipewire-session-manager
	python
	libplasma
	qt6-5compat
	qt6-base
	qt6-declarative
	qt6-multimedia
	qt6-sensors
	qt6-tools
	qt6-wayland
	systemd-libs
	wayland
	xcb-util-cursor
	xcb-util-keysyms
	xcb-util-wm)
makedepends=(extra-cmake-modules
	kdoctools
	krunner
	plasma-wayland-protocols
	python
	wayland-protocols
	xorg-xwayland)
optdepends=('maliit-keyboard: virtual keyboard for kwin-wayland')
groups=(plasma)
source=(https://download.kde.org/stable/plasma/$_dirver/$pkgname-$pkgver.tar.xz{,.sig}
	spurious-dnd.patch)
install=$pkgname.install
sha256sums=('f15108a993206b962a3c5835b988a0b4922c0a9bc9ab80faf6b36a334d321b33'
	'SKIP'
	'e078f88e2e0a46afd1e69f519808cf75085b07c58431bf7da428955e36288687')
validpgpkeys=('E0A3EB202F8E57528E13E72FD7574483BB57B18D' # Jonathan Esk-Riddell <jr@jriddell.org>
	'D7574483BB57B18D'                                      # Jonathan Esk-Riddell
	'0AAC775BB6437A8D9AF7A3ACFE0784117FBCE11D'              # Bhushan Shah <bshah@kde.org>
	'D07BD8662C56CB291B316EB2F5675605C74E02CF'              # David Edmundson <davidedmundson@kde.org>
	'1FA881591C26B276D7A5518EEAAF29B42A678C20')             # Marco Martin <notmart@gmail.com>

prepare() {
	cd $pkgname-$pkgver
	patch --forward --strip=2 --input=../spurious-dnd.patch
}

build() {
	cmake -B build -S $pkgname-$pkgver \
		-DCMAKE_INSTALL_LIBEXECDIR=lib \
		-DBUILD_TESTING=OFF
	cmake --build build
}

package() {
	DESTDIR="$pkgdir" cmake --install build
}
