# Maintainer:  kfgz <kfgz at interia pl>
# Contributor: James Duley <jagduley gmail>
# Contributor: Allan McRae <allan at archlinux dot org>
# Contributor: Tom Newsom <Jeepster at gmx dot co dot uk>

pkgname=xdelta
pkgver=1.1.4
pkgrel=6
pkgdesc='Binary file delta generator'
arch=('x86_64' 'i686')
url="http://sourceforge.net/projects/xdelta/"
license=('GPL')
depends=('glib2' 'zlib')
#options=('!libtool')
source=("http://xdelta.googlecode.com/files/$pkgname-$pkgver.tar.gz"
        'xdelta-1.1.4-pkgconfig.patch'
        'xdelta-1.1.4-m4.patch'
        'xdelta-1.1.4-glib2.patch')
sha256sums=('345503b60432812840991ea1d79cb10db5f34bfaba9499bd0e7d5c57ac5d5c6d'
            '1a00aad31265a5a5b8b6bbfc4c6dd57f08566c72aa4a85fdbea3f9394c4214f4'
            '8a3e06cfef18ed4e976daecab0e4ebdea20dd849136ef919787f4444b8f89f2d'
            'dea479d7c6e116abd72076063adcb790226966eb720a99ffeecd77c4d22a8c03')

prepare() {
  cd ${pkgname}-${pkgver}

  patch -Np1 -i "${srcdir}"/xdelta-1.1.4-m4.patch
  patch -Np1 -i "${srcdir}"/xdelta-1.1.4-glib2.patch
  patch -Np1 -i "${srcdir}"/xdelta-1.1.4-pkgconfig.patch

  autoreconf -vi
}

build() {
  cd ${pkgname}-${pkgver}

  ./configure --prefix=/usr --mandir=/usr/share/man
  make
}

package() {
  make -C ${pkgname}-${pkgver} DESTDIR=${pkgdir} install
}

