# $Id: PKGBUILD 75224 2012-08-16 11:15:20Z bluewind $
# Maintainer: Jan de Groot <jgc@archlinux.org>
# Contributor: John Proctor <jproctor@prium.net>

_pkgbasename=libxml2
pkgname=lib32-$_pkgbasename
pkgver=2.8.0
pkgrel=1
pkgdesc="XML parsing library, version 2 (32-bit)"
arch=(x86_64)
license=('custom')
depends=('lib32-zlib>=1.2.4' 'lib32-readline>=6.1' 'lib32-ncurses>=5.7' $_pkgbasename)
makedepends=(gcc-multilib)
options=('!libtool')
url="http://www.xmlsoft.org/"
source=(ftp://ftp.xmlsoft.org/${_pkgbasename}/${_pkgbasename}-${pkgver}.tar.gz)
md5sums=('c62106f02ee00b6437f0fb9d370c1093')

build() {
  export CC="gcc -m32"
  export CXX="g++ -m32"
  export PKG_CONFIG_PATH="/usr/lib32/pkgconfig"

  cd "${srcdir}/${_pkgbasename}-${pkgver}"
  autoreconf -fi
  ./configure --prefix=/usr --with-threads --with-history --libdir=/usr/lib32 --without-lzma
  make
}

package() {
  cd "${srcdir}/${_pkgbasename}-${pkgver}"
  make DESTDIR="${pkgdir}" install

  rm -rf "${pkgdir}"/usr/{include,share,bin} "$pkgdir/usr/lib32/xml2Conf.sh"
  mkdir -p "$pkgdir/usr/share/licenses"
  ln -s $_pkgbasename "$pkgdir/usr/share/licenses/$pkgname"
}
