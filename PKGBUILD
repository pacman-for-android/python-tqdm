# Maintainer: Felix Yan <felixonmars@archlinux.org>

pkgbase=python-tqdm
pkgname=('python-tqdm' 'python2-tqdm')
pkgver=4.19.9
pkgrel=1
pkgdesc='Fast, Extensible Progress Meter'
arch=('any')
license=('MIT' 'MPL')
url='https://github.com/tqdm/tqdm'
makedepends=('python-setuptools' 'python2-setuptools')
checkdepends=('python-nose' 'python2-nose' 'python-coverage' 'python2-coverage' 'flake8'
              'python2-flake8')
source=("$pkgbase-$pkgver.tar.gz::https://github.com/tqdm/tqdm/archive/v$pkgver.tar.gz")
sha512sums=('fc2b948f880a92c61e7922b7cb442a4cc25296894f858dda77301a272bd50fd5d27d0ef5a8068da22b62e0d8d4d379865ae00ea077ed37418fee35ff359232e6')

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
