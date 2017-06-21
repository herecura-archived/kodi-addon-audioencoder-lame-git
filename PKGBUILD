# $Id$
# Maintainer: BlackEagle <ike.devolder@gmail.com>>

_gitname=kodi-addon-audioencoder-lame
pkgname="$_gitname-git"
_commit=6a250f9
pkgver=20170620.6a250f9
pkgrel=1
pkgdesc="LAME Audio Encoder add-on for Kodi"
arch=('i686' 'x86_64')
url='https://github.com/xbmc/audioencoder.lame'
license=('GPL')
groups=('kodi-addons' 'kodi-addons-audioencoder')
provides=('kodi-audioencoder-lame')
replaces=('kodi-audioencoder-lame')
depends=('kodi-git' 'lame')
makedepends=('git' 'cmake' 'kodi-dev-git')
source=("$_gitname::git://github.com/xbmc/audioencoder.lame.git#commit=$_commit")
sha256sums=('SKIP')

pkgver() {
	cd "$_gitname"
	git log -1 --date=short --format="%cd.%h" | tr -d '-'
}

build() {
	cd "$_gitname"
	cmake \
		-DCMAKE_INSTALL_PREFIX=/usr \
		-DCMAKE_BUILD_TYPE=Release \
		-DBUILD_SHARED_LIBS=1 \
		-DUSE_LTO=1
	make
}

package() {
	cd "$_gitname"
	make DESTDIR="$pkgdir/" install
}

