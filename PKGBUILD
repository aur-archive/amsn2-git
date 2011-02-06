# Contributor: Emanuele Rossi <newdna1510@yahoo.it>
# Contributor: Alessio Biancalana <dottorblaster@gmail.com>
# Contributor: Odites <odites@gmail.com>

pkgname=amsn2-git
_pkgname=amsn2
pkgver=20110120
pkgrel=1
pkgdesc="New Generation of AMSN"
url="http://github.com/drf/amsn2/tree"
license=('GPL')
arch=('i686' 'x86_64')
depends=('python2' 'pygtk' 'libmimic' 'python2-qt' 'papyon-git' 'pycrypto' 'pyopenssl' 'python-imaging')
makedepends=('git')
conflicts=()
replaces=('amsn2-svn')
provides=('amsn2')
source=('amsn2.run' 'amsn2.desktop')
install=('amsn2.install')
md5sums=('30e5831ebf33f3bc2a91e4589a9ced5d'
         '3cb40821e951f1bf99c62b4eff883bef')

_gitroot='git://github.com/amsn/amsn2.git'
_gitname='amsn2'

build() {
set -e

cd "$srcdir"

msg "Connecting to github.com GIT server...."

if [ -d ${srcdir}/$_gitname ] ; then
cd $_gitname
git pull . master
git submodule update --init
msg "The local files are updated."
else
git clone $_gitroot $_gitname
cd $_gitname
git submodule update --init
fi

msg "GIT checkout done."

# Copying files
mkdir -p $startdir/pkg/usr/bin
mkdir -p $startdir/pkg/usr/share/${_pkgname}

cp -r $srcdir/$_gitname/* $startdir/pkg/usr/share/${_pkgname}

# install startup file
install -Dm755 $startdir/src/${_pkgname}.run $startdir/pkg/usr/bin/${_pkgname}

# install desktop file
install -Dm644 $startdir/src/${_pkgname}.desktop $startdir/pkg/usr/share/applications/${_pkgname}.desktop
}
