
# Maintainer: Mamy Ratsimbazafy <mamy (dot) ratsimbazafy_pkgbuild [at] gadz (dot) org>

pkgname=python-chainer-cupy-cudnn-git
_pkgname=chainer
pkgver=v4.0.0b3.r0.ga5fde6f74
pkgrel=1
pkgdesc='NumPy-like API accelerated with CUDA'
arch=('any')
url='https://github.com/chainer/chainer'
license=('custom')
depends=('python-numpy' 'python-six' 'cuda' 'cudnn' 'python-fastrlock' 'python-cupy-cudnn-git')
makedepends=('git' 'python-setuptools')
conflicts=('python-chainer')
provides=('python-chainer')
source=('git://github.com/chainer/chainer.git')
md5sums=('SKIP' )

pkgver() {
  cd $_pkgname
  git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}


build() {
  cd $_pkgname
  export CUDA_PATH=/opt/cuda
#  export CC=gcc-6
#  export CXX=g++-6
  python setup.py build
}

package() {
  cd $_pkgname

  export CUDA_PATH=/opt/cuda
#  export CC=gcc-6
#  export CXX=g++-6
  python setup.py install --root=${pkgdir} --optimize=1

  install -D -m644 LICENSE ${pkgdir}/usr/share/licenses/python-$_pkgname
}
