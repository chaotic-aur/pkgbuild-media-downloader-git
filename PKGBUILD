# Maintainer: willemw <willemw12@gmail.com>

pkgname=media-downloader-git
pkgver=2.4.0.r56.g7c467b0-1
pkgrel=1
pkgdesc="GUI front-end for downloading media files (youtube-dl, ...)"
arch=('x86_64')
url='https://github.com/mhogomchungu/media-downloader'
license=('GPL')
depends=('qt5-base') 
makedepends=('cmake' 'git' 'yt-dlp-git' 'you-get' 'youtube-dl' 'gallery-dl' 'wget' 'aria2')
#optdepends=('wget: download files' 'youtube-dl: download files') 
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
source=("$pkgname::git+$url.git")
sha256sums=('SKIP')

pkgver() {
  git -C $pkgname describe --long | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

build() {
  cmake -B build -S $pkgname -DCMAKE_BUILD_TYPE=None -DCMAKE_INSTALL_PREFIX=/usr -Wno-dev
  make -C build
}

package() {
  make -C build DESTDIR="$pkgdir/" install
}
