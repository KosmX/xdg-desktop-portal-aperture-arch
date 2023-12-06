_pkgname=xdg-desktop-portal-aperture
pkgname="${_pkgname}-git"
pkgver=r26.2934c39
pkgrel=1
url='https://github.com/kosmx/xdg-desktop-portal-aperture'
pkgdesc='xdg-desktop-portal backend for configuration, completely DE independent.'
#pkgdesc='The cake is a lie'
arch=('x86_64' 'aarch64')
license=('MIT')
depends=('xdg-desktop-portal' 'qt6-base')
makedepends=('git' 'cmake' 'qt6-base')
source=("${_pkgname}::git+${url}.git")
sha256sums=('SKIP')

build() {
    cmake -B build -S "$_pkgname" \
        -DCMAKE_BUILD_TYPE='None' \
        -DCMAKE_INSTALL_PREFIX='/usr' \
        -Wno-dev
    cmake --build build
}

check() {
    ctest --test-dir build --output-on-failure
}

package() {
    DESTDIR="$pkgdir" cmake --install build
}

pkgver() {
  cd "${_pkgname}"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short=7 HEAD)"
}
