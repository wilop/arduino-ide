pkgname=arduino-ide
pkgver=2.3.10
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
sha256sums=('cc8a0b01e763d4646b670ce70c1bc8c389a0fa14ab556dcc0749c03f475a7975'
            '305bf99773e4dbf2331adaf4043f6d2f24191d9044e4c9cee67cc7b4d8664cb9')
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

