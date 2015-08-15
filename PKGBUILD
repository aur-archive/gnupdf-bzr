# Contributor: Stefan Husmann <stefan-husmann@t-online.de>
pkgname=gnupdf-bzr
pkgver=969
pkgrel=3
pkgdesc="library to implement the PDF file format"
arch=('i686' 'x86_64')
url="http://www.gnupdf.org"
license=('GPL')
depends=('check' 'libjpeg' 'jbig2dec' 'curl' 'libgcrypt')
makedepends=('bzr' 'awk' 'texi2html' 'texinfo')
provides=('gnupdf')
conflicts=('gnupdf')
source=(gnupdf::bzr+http://bzr.savannah.gnu.org/r/pdf/libgnupdf/trunk/)
md5sums=('SKIP')
_bzrmod="gnupdf"

pkgver() {
  cd $srcdir/$_bzrmod
  bzr revno
}

prepare() {
  cd $srcdir/$_bzrmod/doc
  sed -i '41s+@sp$+@sp 1+' gnupdf-utils.texi
}

build() {
  cd $srcdir/$_bzrmod

  ./autogen.sh
  ./configure --enable-largefiles --prefix=/usr 
  make 
}

package() {
  cd $srcdir/$_bzrmod
  make DESTDIR="$pkgdir/" install 
} 
