# Maintainer: Eric Vidal <eric@obarun.org>
# based on the original aur3 http://pkgbuild.com/git/aur-mirror.git/tree/obshutdown-git/PKGBUILD
# 						Contributor: dragonn <dragonn at op dot pl>

pkgname=obshutdown-git
pkgver=20120701
pkgrel=3
pkgdesc='Openbox shutdown manager'
arch=('i686' 'x86_64')
license=('GPL')
depends=('gtk2' 'cairo')
makedepends=('git')
source=()
sha1sums=()
conflicts=('obshutdown')
url="https://github.com/panjandrum"
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal

_gitroot="https://github.com/panjandrum/obshutdown.git"
_gitname="obshutdown"

build() {
  cd "${srcdir}"
  msg "Connecting to the GIT server...."
  
  if [[ -d "${srcdir}/${_gitname}" ]] ; then
    cd "${_gitname}"
    git pull origin
    msg "The local files are updated."
  else
    git clone "${_gitroot}"
  fi
  
 msg "GIT checkout done or server timeout"
 msg "Starting build..." 

  cd "${srcdir}/${_gitname}"
	autoreconf -f -i -Wall,no-obsolete
	./configure \
		--prefix=/usr 
		
	make
}

package() {
	cd "${srcdir}/${_gitname}"
	make DESTDIR="${pkgdir}" install
}
