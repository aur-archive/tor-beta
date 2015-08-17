# Maintainer: ryan <ryan.roper+aur@gmail.com>
pkgname=tor-beta
pkgver=0.2.3.17
pkgrel=1
pkgdesc="An anonymizing overlay network for TCP"
arch=(i686 x86_64)
url="http://tor.eff.org"
license=(GPL)
provides=(tor)
conflicts=(tor)
install=tor.install
depends=('openssl' 'zlib' 'libevent>=1.3d')
source=("http://www.torproject.org/dist/tor-$pkgver-beta.tar.gz" "tor.conf" "tor.rc")

build() {
  cd $srcdir/tor-$pkgver-beta
  ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
  make || return 1

	mkdir -p $pkgdir/var/lib
	install -o43 -g43 -d -m0700 $pkgdir/var/lib/tor
	install -D -m644 $srcdir/tor.conf $pkgdir/etc/tor/torrc
	install -D -m755 $srcdir/tor.rc $pkgdir/etc/rc.d/tor
	
  make DESTDIR=$pkgdir install
  mv $pkgdir/etc/tor/torrc.sample $pkgdir/etc/tor/torrc-dist
}
# vim: ft=sh sw=2 ts=2
md5sums=('d07158942df1c9e869a25a8a53446862'
         '56c75d4e8a66f34167d31e38c43793dd'
         '4e39d56f462fc9f59e91715ac1b994c0')
