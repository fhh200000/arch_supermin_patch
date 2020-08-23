# Maintainer: Robin Broda <coderobe @ archlinux.org>
# Contributor: Xiao-Long Chen <chenxiaolong@cxl.epac.to>
# Contributor:  Achilleas Pipinellis <axilleas archlinux gr>

pkgname=supermin
pkgver=5.2.0
pkgrel=2
pkgdesc="Tool for creating supermin appliances"
arch=('x86_64')
url="http://people.redhat.com/~rjones/supermin/"
license=('GPL')
makedepends=('ocaml' 'ocaml-findlib' 'cpio')
depends=('e2fsprogs' 'pacman' 'pacman-contrib')
conflicts=('febootstrap<=3.21')
source=("http://download.libguestfs.org/${pkgname}/5.2-stable/${pkgname}-${pkgver}.tar.gz"
        "pacman-iter.patch"
        "pacman-version.patch")
sha512sums=('782d00f95a37ad75833b659300b085b5c7bfa1c795eae9aa57b3c52cab0332d6e6b8e1bddc5b1c0075cc64b60e22b64387771cd9f457568408889244a4628467'
            'cec4e3fa3a82393397fc73b3e99fa4bbc17805f0a08917564cf456060349e56699f69a69a68e1523a052d8d27764cc7bcf619c6b83ff90c664c4784afafab337'
            'SKIP')
validpgpkeys=('F7774FB1AD074A7E8C8767EA91738F73E1B768A0') # Richard W.M. Jones <rjones@redhat.com>

prepare() {
  cd "${pkgname}-${pkgver}"

  patch src/ph_pacman.ml "${srcdir}/pacman-iter.patch"
}

build() {
  cd "${pkgname}-${pkgver}"

  ./configure --prefix=/usr

  make
}

package() {
  cd "${pkgname}-${pkgver}"

  make DESTDIR="${pkgdir}/" install
}
