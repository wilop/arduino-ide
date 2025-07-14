pkgname=arduino-ide
pkgver=2.3.6
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
        "https://www.arduino.cc/wiki/370832ed4114dd35d498f2f449b4781e/arduino.svg"
        "arduino-ide.desktop")
sha256sums=('33bf2cb868abf92b3d160f7433dcd6348cec1c9e633b5c9e1c761f630f87b82b'
            '4137981bcb4057c2e0092f22faea287767f102e0b48497d22cd55e8d6988e4ac'
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
	install -Dm644 "$srcdir/arduino.svg" "$pkgdir/usr/share/pixmaps/arduino-ide.svg"
}

