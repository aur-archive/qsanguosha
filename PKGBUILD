# Maintainer: xgdgsc at gmail dot com
pkgname=qsanguosha

pkgver=20130320
pkgrel=1
pkgdesc="Q-Sanguosha 太阳神三国杀"
arch=('i686' 'x86_64')
url="http://gamux.org/qsanguosha/"
license=('GPL2')
depends=('qt4')
makedepends=('swig' 'make')
source=('http://gamux.org/clientgame/qsanguosha/newqsgs-20130320.tar.gz')
_src_name=newqsgs
#install=qsanguosha.install
md5sums=('63152d67aa32e8e4081271943bc99100')


build() {
   cd "$srcdir/$_src_name-$pkgver"
   sed -i 's/shell uname -p/shell uname -m/' Makefile.conf
   ./configure
   sed -i 's/qmake/qmake-qt4/' Makefile
   sed -i 's/lrelease/lrelease-qt4/' Makefile
   sed -i 's/qmake/qmake-qt4/' src/linux.mk 
   sed -i '263iINCLUDEPATH += /usr/include/qt4' src/QSanguosha.pro
   make
}

package(){
   cd "$srcdir/$_src_name-$pkgver"
   sed -i 's|PREFIX:=$(DESTDIR)/usr|PREFIX:='"$pkgdir"'/usr|' Makefile
   make install
   mkdir -p "$pkgdir/usr/bin"
   ln -s /usr/games/QSanguosha "$pkgdir/usr/bin/QSanguosha"
}
