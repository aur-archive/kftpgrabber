# Contributor: Andrea Scarpino <andrea@archlinux.org>
# Contributor: Eric Belanger <eric@archlinux.org>
# Contributor : mutlu_inek <mutlu_inek@yahoo.de>

pkgname=kftpgrabber
pkgver=0.8.1
pkgrel=4
pkgdesc="A graphical FTP client for KDE"
arch=('i686' 'x86_64')
url="http://www.kftp.org/"
license=('GPL')
depends=('gcc-libs' 'zlib' 'libx11' 'kdelibs3')
options=('libtool')
source=("http://www.kftp.org/uploads/files/${pkgname}-${pkgver}.tar.bz2"
        'kftpgrabber-0.8.1-glibc-2.10.patch'
	'gcc4.4.patch'
	'openssl1.patch')
md5sums=('56610fd3e2e7f092b7d8eed10d3e5d36'
	'e3e70ce688a6161dc8a15b569b8fceb0'
	'c0ed1df2a418d15c0367067972194cc9'
	'5e1b5e4d7858cc1862b5791b4abe6d31')

build() {
  cd ${srcdir}/${pkgname}-${pkgver}
  patch -p1 -i ${srcdir}/kftpgrabber-0.8.1-glibc-2.10.patch || return 1
  patch -Np1 -i ${srcdir}/gcc4.4.patch || return 1
  patch -Np1 -i ${srcdir}/openssl1.patch || return 1
  . /etc/profile.d/kde3.sh
  ./configure --prefix=/opt/kde \
    --without-arts || return 1
  make || return 1
}

package() {
  cd ${srcdir}/${pkgname}-${pkgver}
  make DESTDIR="${pkgdir}" install || return 1
}
