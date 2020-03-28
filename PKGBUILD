## $Id$
# Contributor: TheKit <nekit1000 at gmail.com>
# Contributor: Alexey Andreyev <aa13q@ya.ru>
# Maintainer: James Kittsmiller (AJSlye) <james@nulogicsystems.com>

_name=quickcontrols-nemo
pkgname=qt5-$_name-git
pkgver=5.3.13.r13.g63d6da1
pkgrel=1
pkgdesc="Nemomobile Qt Quick Controls"
arch=('x86_64' 'aarch64')
url="https://github/nemomobile/qt$_name"
license=('GPL')
depends=('qt5-base' 'qt5-quickcontrols')
makedepends=('git')
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
source=("git+https://github.com/nemomobile/qt$_name.git")
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/qt$_name"
  ( set -o pipefail
    git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g' ||
    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
  ) 2>/dev/null
}

build() {
  cd "$srcdir/qt$_name"
  mkdir -p build
  cd build
  qmake ..
  make
}

package() {
  cd "$srcdir/qt$_name"
  cd build
  make INSTALL_ROOT="${pkgdir}" install
}
