# Maintainer: Hu Butui <hot123tea123@gmail.com>

_realname=dlpack
pkgbase=mingw-w64-${_realname}
pkgname=("${MINGW_PACKAGE_PREFIX}-${_realname}")
pkgver=0.6
pkgdesc="Common in-memory tensor structure"
pkgrel=1
arch=('any')
mingw_arch=('mingw32' 'mingw64' 'ucrt64' 'clang64' 'clang32')
url="https://github.com/dmlc/dlpack"
license=('Apache')
makedepends=("${MINGW_PACKAGE_PREFIX}-cmake")
source=("${_realname}-${pkgver}.tar.gz::https://github.com/dmlc/dlpack/archive/refs/tags/v${pkgver}.tar.gz")
sha256sums=('ce7715108623c011aa1e01afb32e218ddbdf66492494d7e718a78ac41010b77a')

build() {
  MSYS2_ARG_CONV_EXCL="-DCMAKE_INSTALL_PREFIX=" \
  ${MINGW_PREFIX}/bin/cmake.exe \
    -B "${srcdir}/build-${MINGW_CHOST}" \
    -S ${_realname}-${pkgver} \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=${MINGW_PREFIX} \
    -DBUILD_MOCK=OFF \
    -G'MSYS Makefiles'
  ${MINGW_PREFIX}/bin/cmake.exe --build "${srcdir}/build-${MINGW_CHOST}"
}

package() {
  DESTDIR="${pkgdir}" \
  ${MINGW_PREFIX}/bin/cmake.exe \
    --build "${srcdir}/build-${MINGW_CHOST}" \
    --target install
}
