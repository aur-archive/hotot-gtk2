# Maintainer: speps <speps at aur dot archlinux dot org>

_uname=lyricat
_commit=1f68d33
pkgname=hotot-gtk2
pkgver=0.9.8.14
pkgrel=1
pkgdesc="A lightweight & open source microblogging software (twitter identi.ca). Gtk2 frontend."
arch=('any')
url="http://www.hotot.org/"
license=('LGPL3')
depends=('hotot-data' 'pywebkitgtk' 'python2-notify' 'python2-pycurl'
         'python2-keybinder2' 'python2-dbus' 'desktop-file-utils')
optdepends=('libappindicator: unity menubar integration')
makedepends=('cmake' 'intltool')
install="hotot-gtk2.install"
source=("https://github.com/$_uname/Hotot/archive/$pkgver.tar.gz")
md5sums=('7437f5132a50f7239e1b4bd09f410a17')

build() {
  cd ${srcdir}/Hotot-*
  [ -d bld ] || mkdir bld && cd bld
  cmake .. -DCMAKE_INSTALL_PREFIX=/usr \
           -DWITH_GTK=ON \
           -DWITH_GTK2=ON \
           -DWITH_GIR3=OFF \
           -DWITH_QT=OFF \
           -DWITH_QT5=OFF \
           -DWITH_CHROME=OFF \
           -DPYTHON_EXECUTABLE=/usr/bin/python2
  make
}

package() {
  cd ${srcdir}/Hotot-*/bld/hotot
  DESTDIR="$pkgdir/" cmake -P cmake_install.cmake

  # bin
  install -Dm755 ../scripts/$pkgname \
    "$pkgdir/usr/bin/$pkgname"

  # desktop file
  install -Dm644 ../misc/$pkgname.desktop \
    "$pkgdir/usr/share/applications/$pkgname.desktop"
}

# vim:set ts=2 sw=2 et:
