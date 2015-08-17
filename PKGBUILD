# Maintainer: Gonzalo Jose Hernandez <GonzaloHernandez@udenar.edu.co>
# Contributor: Gonzalo Jose Hernandez <GonzaloHernandez@udenar.edu.co>
pkgname=python-httpserver-frontend
pkgver=11
pkgrel=1
pkgdesc="Python SimpleHttpServer Frontend"
arch=('i686' 'x86_64')
url="https://code.google.com/p/python-httpserver-frontend"
license=('GPL')
depends=('qt5-base' 'icu' 'python')
makedepends=('subversion')
provides=(python-httpserver-frontend)
conflicts=(python-httpserver-frontend)
source=()
md5sums=()
 
_svntrunk="https://python-httpserver-frontend.googlecode.com/svn/trunk/"
_svnmod=python-httpserver-frontend
 
build() {
  cd $srcdir
  msg "Connecting to SVN server...."
  if [ -d $_svnmod/.svn ]; then
    (cd $_svnmod && svn up -r $pkgver)
  else
    svn co $_svntrunk --config-dir ./ -r $pkgver $_svnmod
  fi
 
  msg "SVN checkout done or server timeout"
  msg "Starting make..."
  svn export $_svnmod $_svnmod-build
  cd $_svnmod-build
  qmake -o Makefile $srcdir/python-httpserver-frontend/python-httpserver-frontend.pro
  make
}
 
package() {
  mkdir -p $pkgdir/usr/bin
  mkdir -p $pkgdir/usr/share/applications
  mkdir -p $pkgdir/usr/share/icons
  install -m 755 -D $srcdir/$pkgname-build/$pkgname $pkgdir/usr/bin/
  cd ..
  install -m 755 -D $pkgname.desktop $pkgdir/usr/share/applications/
  install -m 755 -D $pkgname.png $pkgdir/usr/share/icons/  
}
