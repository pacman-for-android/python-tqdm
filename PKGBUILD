# Maintainer: Felix Yan <felixonmars@archlinux.org>

pkgbase=python-tqdm
pkgname=('python-tqdm' 'python2-tqdm')
pkgver=4.23.2
pkgrel=1
pkgdesc='Fast, Extensible Progress Meter'
arch=('any')
license=('MIT' 'MPL')
url='https://github.com/tqdm/tqdm'
makedepends=('python-setuptools' 'python2-setuptools')
checkdepends=('python-nose' 'python2-nose' 'python-coverage' 'python2-coverage' 'flake8'
              'python2-flake8')
source=("$pkgbase-$pkgver.tar.gz::https://github.com/tqdm/tqdm/archive/v$pkgver.tar.gz")
sha512sums=('61f4303ae1297629d9c0c112f83955561f544eb02261dddd08c5bb7e110c5affe8f63cda0738869bf38de67372266168d0ed92a7191573baf25e252610754693')

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
