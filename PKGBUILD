# Maintainer: Martin Kostolný <clearmartin at zoho dot com>

pkgname=plasma-applet-weather-widget-git
_pkgname=plasma-applet-weather-widget
pkgver=r15.6241400
pkgrel=1
pkgdesc="Plasmoid for Plasma 5. Shows weather information from yr.no server."
arch=('any')
url="https://github.com/kotelnik/$_pkgname"
license=('GPL')
depends=('plasma-workspace' 'qt5-graphicaleffects')
makedepends=('git' 'extra-cmake-modules')
conflicts=("${pkgname%-*}")
provides=("${pkgname%-*}")
source=("git://github.com/kotelnik/$_pkgname.git")
md5sums=('SKIP')

pkgver() {
  cd "${_pkgname}"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  cd "${_pkgname}"
  
  mkdir -p build
  cd build
  rm -rf *
  
  cmake .. \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_BUILD_TYPE=Release \
    -DLIB_INSTALL_DIR=lib \
    -DKDE_INSTALL_USE_QT_SYS_PATHS=ON
}

package() {
  cd "${_pkgname}"/build
  
  make install DESTDIR="${pkgdir}"
}
