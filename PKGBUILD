# Maintainer: Felix Yan <felixonmars@archlinux.org>

pkgbase=python-tqdm
pkgname=('python-tqdm' 'python2-tqdm')
pkgver=4.20.0
pkgrel=1
pkgdesc='Fast, Extensible Progress Meter'
arch=('any')
license=('MIT' 'MPL')
url='https://github.com/tqdm/tqdm'
makedepends=('python-setuptools' 'python2-setuptools')
checkdepends=('python-nose' 'python2-nose' 'python-coverage' 'python2-coverage' 'flake8'
              'python2-flake8')
source=("$pkgbase-$pkgver.tar.gz::https://github.com/tqdm/tqdm/archive/v$pkgver.tar.gz")
sha512sums=('4c1974e2858d6251132b5208edee34f45e2d435891d97f837006d2a1baeca14dcbf290a594c18dc2ba936fdd69a53a9c6d460a23c5c04ef8f9e8c3e78d109478')

prepare() {
  cp -a tqdm-$pkgver{,-py2}
}

build() {
  cd "$srcdir"/tqdm-$pkgver
  python setup.py build

  cd "$srcdir"/tqdm-$pkgver-py2
  python2 setup.py build
}

check() {
  cd "$srcdir"/tqdm-$pkgver
  python setup.py nosetests --ignore-files="tests_perf\.py"

  cd "$srcdir"/tqdm-$pkgver-py2
  python2 setup.py nosetests --ignore-files="tests_perf\.py"
}

package_python-tqdm() {
  depends=('python')

  cd tqdm-$pkgver
  python setup.py install --root="$pkgdir" --optimize=1
  install -D -m644 LICENCE "$pkgdir"/usr/share/licenses/$pkgname/LICENCE

  mv "$pkgdir"/usr/{,share/}man
}

package_python2-tqdm() {
  depends=('python2')

  cd tqdm-$pkgver-py2
  python2 setup.py install --root="$pkgdir" --optimize=1
  install -D -m644 LICENCE "$pkgdir"/usr/share/licenses/$pkgname/LICENCE

  mv "$pkgdir"/usr/bin/tqdm{,2}
  mv "$pkgdir"/usr/{,share/}man
  mv "$pkgdir"/usr/share/man/man1/tqdm{,2}.1
}

# vim:set ts=2 sw=2 et:
