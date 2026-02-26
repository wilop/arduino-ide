pkgname=arduino-ide
pkgver=2.3.8
pkgrel=1
pkgdesc="Arduino IDE 2.x: The open-source software for programming Arduino boards (binary version)."
arch=(x86_64)
url="https://github.com/arduino/arduino-ide"
license=(AGPL3)
depends=(libxkbfile libxss nss libsecret git)
optdepends=('libusb: To directly communicate with USB devices'
            'usbutils: For querying and inspecting USB devices'
            'libusb-compat: An old version of libusb (legacy support)'
            'python-pyserial: For serial communication')
makedepends=(unzip)
provides=(arduino-ide)
options=(!strip)
source=("https://github.com/arduino/arduino-ide/releases/download/${pkgver}/arduino-ide_${pkgver}_Linux_64bit.zip"
        "arduino-ide.desktop")
sha256sums=('226932e402fbdd6763f3988257cf0f69050934f92cdd01ede9dab99e1a238bdb'
            'SKIP')
noextract=(arduino-ide_${pkgver}_Linux_64bit.zip)

prepare() {
	mkdir -p "$srcdir/arduino-ide"
	unzip "$srcdir/arduino-ide_${pkgver}_Linux_64bit.zip" -d "$srcdir/arduino-ide"
}

package() {
	install -dm755 "$pkgdir/opt/"
	chmod -R 755 "arduino-ide"
	cp -r "$srcdir/arduino-ide/arduino-ide_${pkgver}_Linux_64bit" "$pkgdir/opt/arduino-ide"
	install -dm755 "$pkgdir/usr/bin"
	ln -s "/opt/arduino-ide/arduino-ide" "$pkgdir/usr/bin/arduino-ide"
	install -Dm644 "$srcdir/arduino-ide.desktop" "$pkgdir/usr/share/applications/arduino-ide.desktop"
	install -Dm644 "$srcdir/arduino-ide/arduino-ide_${pkgver}_Linux_64bit/resources/app/resources/icons/512x512.png" "$pkgdir/usr/share/pixmaps/arduino-ide.png"
}

