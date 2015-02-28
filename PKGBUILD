pkgname=bomi
pkgver=0.9.2
pkgrel=1
pkgdesc="Powerful and easy-to-use GUI multimedia player based on mpv"
arch=('x86_64')
url="http://$pkgname-player.github.io"
license=('GPL')
provides=('cmplayer')
install=$pkgname.install
depends=('qt5-base' 'qt5-declarative' 'qt5-x11extras' 'qt5-quickcontrols' 'icu'
         'libdvdread' 'libdvdnav' 'libcdio-paranoia' 'libcdio'
         'alsa-lib' 'libpulse' 'jack' 'libchardet' 'libbluray'
         'mpg123' 'libva' 'libgl' 'fribidi' 'libass' 'ffmpeg')
makedepends=('mesa' 'gcc' 'pkg-config' 'python' 'qt5-tools')
optdepends=('libaacs: AACS decryption for Blu-ray support'
            'libbdplus: BD+ decryption for Blu-ray support'
            'youtube-dl: streaming website support including YouTube')
source=($pkgname-$pkgver.tar.gz::https://github.com/xylosper/bomi/archive/v$pkgver.tar.gz)
md5sums=('071e5c2b2e21581eb91aa67ff9630b78')
#options=(debug !strip)

build() {
  cd "$srcdir/$pkgname-$pkgver"
  ./configure --prefix=/usr --enable-jack --enable-cdda --enable-pulseaudio
  sed -i 's/--disable-cplayer/--disable-cplayer --disable-rubberband/g' build-mpv
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  make DEST_DIR=$pkgdir install
}
