# Maintainer: Angel Velasquez <angvp@archlinux.org>  
pkgbase=python-ecdsa
pkgname=('python-ecdsa' 'python2-ecdsa')
pkgver=0.10
pkgrel=1
pkgdesc="Implementation of ECDSA in Python"
arch=('any')
url="https://github.com/warner/python-ecdsa"
license=('MIT')
makedepends=('python-setuptools' 'python2-setuptools')
options=(!emptydirs)
source=("http://pypi.python.org/packages/source/e/ecdsa/ecdsa-$pkgver.tar.gz" "LICENSE")
md5sums=('e95941b3bcbf1726472bb724d7478551'
         '66ffc5e30f76cbb5358fe54b645e5a1d')

build() {
  cp -R "$srcdir/ecdsa-$pkgver" "$srcdir/ecdsa-$pkgver-py2"
  cd "$srcdir/ecdsa-$pkgver-py2"
  sed -ie 's#/usr/bin/env python#/usr/bin/env python2#' ecdsa/*.py
}

package_python-ecdsa() {
  depends=('python')
  cd "$srcdir/ecdsa-$pkgver"
  python setup.py install --root="$pkgdir/" --optimize=1
  install -D -m644 "$srcdir/LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

package_python2-ecdsa() {
  depends=('python2')
  cd "$srcdir/ecdsa-$pkgver-py2"
  python2 setup.py install --root="$pkgdir/" --optimize=1
  install -D -m644 "$srcdir/LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}