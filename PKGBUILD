# Maintainer: Allonsy <linuxbash8@gmail.com>

DLAGENTS=('http::/usr/bin/wget -c -U Mozilla -t 3 --waitretry=3 -O %o %u')

pkgname=tiemu
pkgver=3.03
pkgrel=5
pkgdesc="TiEmu emulates Texas Instruments calculators TI-89/92/92+/V200PLT (no GDB)."
arch=(i686 x86_64)
url="http://tilp.info/"
license=('GPL')
makedepends=('wget')
depends=('libglade' 'libticalcs' 'sdl')
options=('!libtool')
source=(http://download.sourceforge.net/project/gtktiemu/tiemu-linux/TIEmu%203.03/tiemu-3.03-nogdb.tar.gz
        01-build-fix.patch
        02-new.patch
        log_link.c
		    sysdeps.patch)
md5sums=('2736440d717a0ee97cdb35189814fc93' 
         '3d87b3c7130c9e3bce07f92156c21d70'
         'f0aef5853902819b77d34715688ae22d'
         '6236cac7ee418e85ac44050e0062002c'
		     'e09e54413b912fd86a553bed7865c32e')

build() {
  cd $srcdir/tiemu-$pkgver
  patch -p1 --input ../01-build-fix.patch
  patch -p1 --input ../sysdeps.patch
  ./configure --without-kde --disable-gdb --prefix=/usr
  patch -p0 --input ../02-new.patch
  cp ../../log_link.c src/gui/logger/log_link.c
  make
}

package() 
{
  cd "$srcdir/$pkgname-$pkgver"
  make install prefix="$pkgdir/usr"
}
		
