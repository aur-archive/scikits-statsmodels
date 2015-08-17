# Maintainer: Andrzej Giniewicz <gginiu@gmail.com>
pkgname=scikits-statsmodels
pkgver=0.4.3
pkgrel=1
pkgdesc="Statistical computations and models for use with SciPy"
arch=('i686' 'x86_64')
url="http://scikits.appspot.com/statsmodels"
license=('BSD')
depends=('python2-scipy' 'python2-pandas' 'scikits-base')
makedepends=('python2-distribute' 'cython2')
optdepends=('python2-matplotlib: plotting'
            'python-numdifftools: likelihood models for time series')
options=(!emptydirs)

source=("http://pypi.python.org/packages/source/s/statsmodels/statsmodels-${pkgver}.tar.gz")
md5sums=('eee727c2fa4e3d884f1baaae7ae3d58c')

build() {
  cd "$srcdir"/statsmodels-${pkgver}

  sed -i -e "s/'cython'/'cython2'/" tools/_build.py
  python2 setup.py build
}

package() {
  cd "$srcdir"/statsmodels-${pkgver}

  python2 setup.py install --root="$pkgdir"/ --optimize=1

  rm "$pkgdir/`python2 -c 'from distutils.sysconfig import get_python_lib; \
    print get_python_lib()'`/scikits/__init__.py"

  sed -i -e "s|#![ ]*/usr/bin/env python$|#!/usr/bin/env python2|" \
    $(find "${pkgdir}" -name '*.py')

  install -D LICENSE.txt "$pkgdir"/usr/share/licenses/scikits-statsmodels/LICENSE
}

