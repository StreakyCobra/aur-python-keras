# Maintainer: Fabien Dubosson <fabien.dubosson@gmail.com>

pkgbase="python-keras"
pkgname=("python-keras" "python2-keras")
_pkgname="keras"
pkgver="0.3.2"
pkgrel="1"
pkgdesc="Theano-based Deep Learning library (convnets, recurrent neural networks, and more)"
arch=('i686' 'x86_64')
url="https://github.com/fchollet/keras"
license=('MIT')
makedepends=('python' 'python-setuptools' 'python-numpy' 'python-scipy' 'python-h5py'
             'python2' 'python2-setuptools' 'python2-numpy' 'python2-scipy' 'python2-h5py'
            )
changelog="ChangeLog"
source=("${_pkgname}.tar.gz::https://github.com/fchollet/${_pkgname}/archive/${pkgver}.tar.gz")
sha256sums=('cd2cd768b039703eb9e4a9fac154588a4f36daad53f4c359c241333ee36af7cf')

prepare() {
  cd "$srcdir/"
  cp -a "${_pkgname}-${pkgver}" "${_pkgname}-${pkgver}-py2"
  cd "${_pkgname}-${pkgver}"
  sed -e "s|#![ ]*/usr/bin/python$|#!/usr/bin/python2|" \
      -e "s|#![ ]*/usr/bin/env python$|#!/usr/bin/env python2|" \
      -e "s|#![ ]*/bin/env python$|#!/usr/bin/env python2|" \
      -i $(find . -name '*.py')
}

build() {
  msg "Building Python 2"
  cd "$srcdir/${_pkgname}-${pkgver}-py2"
  python2 setup.py build

  msg "Building Python 3"
  cd "$srcdir/${_pkgname}-${pkgver}"
  python setup.py build
}

package_python2-keras() {
  depends=('python2' 'python2-numpy' 'python2-scipy' 'python2-theano' 'python2-h5py')
  cd "$srcdir/${_pkgname}-${pkgver}-py2"
  python2 setup.py install --root="$pkgdir"/ --optimize=1
}

package_python-keras() {
  depends=('python' 'python-numpy' 'python-scipy' 'python-theano' 'python-h5py')
  cd "$srcdir/${_pkgname}-${pkgver}"
  python setup.py install --root="$pkgdir"/ --optimize=1
}

# vim:set ts=2 sw=2 et:
