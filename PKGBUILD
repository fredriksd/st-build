# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.

# Maintainer: Fredrik Sandhei <fredrik.sandhei@gmail.com>
pkgname=st-fredrik
_pkgname=st
pkgver=0.8.4
pkgrel=1
pkgdesc="My setup of suckless terminal setup."
arch=('x86_64')
url="git://git.suckless.org/st"
license=('MIT')
depends=()
makedepends=(git make)
backup=()
options=('zipman')

source=("git + ${url}"
        "$pkgname-$pkgver.patch")
noextract=()
md5sums=()

provides=("${_pkgname}")

prepare() {
	#cd "$pkgname-$pkgver"
        cd ~/.config/st
	patch -p1 -i "$srcdir/$pkgname-$pkgver.patch"
}

build() {
	cd "$pkgname-$pkgver"
	./configure --prefix=/usr
	make
}

check() {
	cd "$pkgname-$pkgver"
	make -k check
}

package() {
	cd "$pkgname-$pkgver"
	make DESTDIR="$pkgdir/" install
}
