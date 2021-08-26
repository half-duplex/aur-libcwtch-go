# Maintainer: GI Jack <GI_Jack@hackermail.com>

pkgname=libcwtch-go
pkgver=1.1.1
pkgrel=1
pkgdesc="Privacy Preserving Infrastructure for Asynchronous, Decentralized and Metadata Resistant Applications"
arch=('x86_64' 'i686')
url="https://cwtch.im/"
license=('MIT')
depends=('tor')
makedepends=('go')
source=("libcwtch-go-${pkgver}.tar.gz::https://git.openprivacy.ca/cwtch.im/libcwtch-go/archive/v${pkgver}.tar.gz"
        'cwtch.sysusers' 'cwtch.tmpfiles')
sha256sums=('0116e6ba5afb35a7d2f4bb22e3d042f355195026cb3bbc06abc627404f005d5d'
            'beab74c0441b6532c1f4b7365038f595372f7e7a3a4b3587d36a3cb9dc8605fb'
            '399bacb458e108df49dda328258ba0653506393cef465dd794efa3b371fba902')

# Extranious unpackaged deps. Might enable later after packaging these for checkdeps
#check() {
#  cd "${srcdir}/${pkgname}"
#  ./quality.sh
#}

prepare() {
  export GOPATH="${srcdir}/go"
  cd "${srcdir}/${pkgname}"
  make clean
}

build() {
  export GOPATH="${srcdir}/go"
  cd "${srcdir}/${pkgname}"
  make linux
}

package() {
  cd "${srcdir}/${pkgname}"
  
  install -Dm 644 "libCwtch.so" "${pkgdir}/usr/lib/cwtch/libCwtch.so"
  # create user and chown files
  install -Dm0644 "${srcdir}/cwtch.sysusers" "${pkgdir}/usr/lib/sysusers.d/cwtch.conf"
  install -Dm0644 "${srcdir}/cwtch.tmpfiles" "${pkgdir}/usr/lib/tmpfiles.d/cwtch.conf"
}
