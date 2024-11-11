# Maintainer: YourName <youremail@example.com>
pkgname=warzone2100
pkgver=4.5.4  # Update this based on the actual version
pkgrel=1
pkgdesc="A real-time strategy game set in a post-apocalyptic world"
arch=('x86_64')
url="https://wz2100.net/"
license=('GPL')
depends=('qt5-base' 'glew' 'sdl2' 'openal')
makedepends=('cmake' 'git')
source=("git+https://github.com/Warzone2100/warzone2100.git#tag=${pkgver}")
sha256sums=('SKIP')

prepare() {
    cd "${srcdir}/warzone2100"
    git submodule update --init --recursive
}

build() {
    cd "${srcdir}/warzone2100"
    mkdir -p build
    cd build
    cmake .. -DCMAKE_BUILD_TYPE=Release \
             -DCMAKE_INSTALL_PREFIX=/usr \
             -DCMAKE_INSTALL_MANDIR=/usr/share/man \
             -DCMAKE_INSTALL_DATADIR=/usr/share
    make
}

package() {
    cd "${srcdir}/warzone2100/build"
    make DESTDIR="${pkgdir}" install
}

# vim:set ts=2 sw=2 et:

