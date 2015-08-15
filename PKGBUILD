pkgname=dkms-msp430-launchpad-uart-fix
_pkgname=cdc-acm
pkgver=git
pkgrel=3
pkgdesc='DKMS-enabled kernel module fix for the MSP430 LaunchPad UART'
url='https://github.com/energia/Energia/wiki/Linux-Serial-Communication'
arch=('i686' 'x86_64')
license=('custom')
depends=('dkms')
makedepends=('wget')

source=('Makefile'
	'dkms.conf'
	'cdc-acm.patch')
md5sums=('e799f9fc97b5ed54bfe53abc838a3434'
         'eaf1765a344e85c6b339f52acac31f8f'
         '049561904a92e16a782acc024c70cb3a')

install=cdc-acm.install

build() {
	cd "${srcdir}"
	wget 'http://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=blob_plain;f=drivers/usb/class/cdc-acm.c;hb=HEAD' -O cdc-acm.c
	wget 'http://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=blob_plain;f=drivers/usb/class/cdc-acm.h;hb=HEAD' -O cdc-acm.h
	patch -p0 < cdc-acm.patch
}

package() {
	cd "${srcdir}"
	mkdir -p ${pkgdir}/usr/src/${_pkgname}-${pkgver}
	cp -L Makefile ${pkgdir}/usr/src/${_pkgname}-${pkgver}
	cp -L dkms.conf ${pkgdir}/usr/src/${_pkgname}-${pkgver}
	cp -L cdc-acm.{c,h} ${pkgdir}/usr/src/${_pkgname}-${pkgver}
}
