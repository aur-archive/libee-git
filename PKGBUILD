# Maintainer: Brian Knox <taotetek at gmail>
# Submitter: Brian Knox <taotetek at gmail>

pkgname=libee-git
pkgver=20120401
pkgrel=2
pkgdesc="event expression library"
arch=('i686' 'x86_64')
url="http://www.libee.org/"
license=('LGPL')
depends=('gcc-libs' 'libestr-git')
makedepends=('git make')
conflicts=('libee')
provides=('libee')
_gitroot="git://git.adiscon.com/git/libee.git"
_gitname="libee"

build() {
  cd "$srcdir"
  msg "Connecting to Git server...."

  if [ -d $_gitname ]; then
    pushd $_gitname && git pull origin && popd
    msg "The local files are updated"
  else
    git clone $_gitroot
  fi

  msg "Git checkout done or server timeout"
  msg "Starting make..."

  rm -rf $_gitname-build
  git clone $_gitname $_gitname-build
  cd $_gitname-build
}

package() {
  cd "$srcdir/$_gitname-build"
  autoreconf -fvi
  ./configure --prefix=/usr
  make install DESTDIR=${pkgdir}
}
