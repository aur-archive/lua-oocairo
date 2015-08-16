# Contributor: Michal Minar <mr.mini@centrum.cz>
# Maintainer: Zsolt Udvari <udvzsolt@gmail.com>

pkgname=lua-oocairo
pkgver=1.4
pkgrel=4
pkgdesc="Module providing access to the Cairo from within Lua."
arch=(i686 x86_64)
url="http://luaforge.net/projects/oocairo/"
license=('MIT')
depends=("cairo>=1.8.0" "lua>=5.1")
makedepends=("libtool" "pkgconfig")
source=("http://oocairo.naquadah.org/dist/oocairo-${pkgver}.tar.bz2"
    lua52-compatible.patch
    encoding.patch
) 
md5sums=('d39574cdb781a62728758553afef1d31'
         'e54af5cbd99dfd9cecda6b838cbf308b'
         '884bc616c08a0c0282f3a5cef1c93192')

build() {
  cd ${srcdir}/oocairo-${pkgver}
  patch -Np1 -i ${srcdir}/lua52-compatible.patch
  patch -Np1 -i ${srcdir}/encoding.patch
  autoconf
  ./configure --prefix=/usr
  make || return 1
}

package() {
  cd ${srcdir}/oocairo-${pkgver}
  make DESTDIR="$pkgdir" install
  mkdir -p "$pkgdir/usr/share/licenses/lua-oocairo"
  cp COPYRIGHT "$pkgdir/usr/share/licenses/lua-oocairo"
}

# vim:syntax=sh
