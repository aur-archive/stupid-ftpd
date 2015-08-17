# $Id$
# Maintainer: danitool

pkgname=stupid-ftpd
pkgver=1.5beta
pkgrel=2
pkgdesc="stupid-ftpd is an ftp server, which provides a normal ftp-daemon functionality and a command-line mode. It has got a /etc/passwdindependent user database which allows many variations of permissions. The server is easy to configure and very flexible"
arch=('i686' 'x86_64')
url="http://stupid-ftpd.sourceforge.net/"
license=('GPL')
source=("http://downloads.sourceforge.net/project/stupid-ftpd/stupid-ftpd/V1_5beta/$pkgname-$pkgver.tar.gz"
	'stupid-ftpd.service'
	'fixes.patch')
md5sums=('be5700570bc38376515d33595e416663'
	'fc0a7a5f143ef657d8d495a030fa8c20'
	'915b029020af010d9c3072b6a4d17700')
install=post_install

build() {
  cd $srcdir/$pkgname
	patch -p0 -i ${srcdir}/fixes.patch
	make || return 1
}

package() {
  cd $srcdir/$pkgname
	install -D -m755 stupid-ftpd.Linux6 $pkgdir/usr/bin/stupid-ftpd
	#install -D -m644 $srcdir/stupid-ftpd.service $pkgdir/usr/lib/systemd/system/stupid-ftpd.service
	sed -i "39s/real/virtual/g" stupid-ftpd.conf
	sed -i "33cserverroot=/home" stupid-ftpd.conf
	install -D -m644 stupid-ftpd.conf $pkgdir/etc/stupid-ftpd/stupid-ftpd.conf
}
