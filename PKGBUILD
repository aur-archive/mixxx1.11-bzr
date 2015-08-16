# Maintainer: Gimmeapill <gimmeapill at gmail dot com>

pkgname=mixxx1.11-bzr
pkgver=3875
pkgrel=1
pkgdesc="Digital DJ mixing software. Branch 1.11 (stable) from bzr with cpu optimization enabled"
arch=('i686' 'x86_64')
url="http://www.mixxx.org/"
license=('GPL2')
depends=('libid3tag' 'libmad' 'portaudio' 'qt4' 'qtwebkit' 'libogg' 'libvorbis' 'libsndfile' 'taglib' 'portmidi' 'protobuf' 'fftw' 'libusbx')
makedepends=('bzr' 'scons>=0.98' 'pkgconfig>=0.15.0')
optdepends=('faad2: M4A support' 
			'mp4v2: M4A support' 
			'libshout: Shoutcast support'
			'vamp-plugin-sdk: Vamp support')
provides=(mixxx)
conflicts=(mixxx mixxx-bzr mixxx1.8-bzr mixxx1.9-bzr mixxx1.10-bzr mixxx-beta)

_bzrmod=mixxx
_bzrtrunk=lp:${_bzrmod}/1.11

pkgver() {
	cd "$_bzrmod"
	bzr revno
}

build() {
  cd ${srcdir}

  msg "Connecting to the server...."

  if [ ! -d ./${_bzrmod} ]; then
    bzr co ${_bzrtrunk} ${_bzrmod}
  else
    bzr up ${_bzrmod}
    cd ${_bzrmod}
  fi

  msg "BZR checkout done or server timeout"
  msg "Starting make..."

  cd "${srcdir}/${_bzrmod}/${_bzrmod}"

  scons qtdir=/usr/lib/qt4 prefix=/usr install_root=$pkgdir/usr tuned=1
  scons qtdir=/usr/lib/qt4 prefix=/usr install_root=$pkgdir/usr install
}
