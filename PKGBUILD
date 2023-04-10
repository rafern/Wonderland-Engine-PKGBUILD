pkgname=wonderlandengine
pkgver=0.9.5
pkgverfolder=$pkgver
pkgrel=1
pkgdesc="Accessible WebXR focused development platform."
arch=('x86_64')
url="https://wonderlandengine.com"
license=('custom')
depends=('glfw' 'libpng' 'libgl')
provides=('wonderlandengine')
conflicts=('wonderlandengine')
source=("WonderlandEngine-${pkgver//_/-}-Linux.tar.gz::https://downloads.wonderlandengine.com/${pkgverfolder//_/-}/WonderlandEngine-${pkgver//_/-}-Linux.tar.gz")
sha256sums=('SKIP')

package() {
    cd "WonderlandEngine-${pkgver//_/-}-Linux"
    # bin files
    install -dm755 "${pkgdir}/opt/"
    install -dm755 "${pkgdir}/opt/wonderlandengine/"
    chmod -R 755 "bin"
    cp -r "bin" "${pkgdir}/opt/wonderlandengine/bin"
    install -dm755 "${pkgdir}/usr/bin"
    echo "#!/bin/sh" > "${pkgdir}/opt/wonderlandengine/bin/WonderlandEditor.sh"
    echo "exec env LD_LIBRARY_PATH=/opt/wonderlandengine/lib /opt/wonderlandengine/bin/WonderlandEditor \$@" >> "${pkgdir}/opt/wonderlandengine/bin/WonderlandEditor.sh"
    chmod 755 "${pkgdir}/opt/wonderlandengine/bin/WonderlandEditor.sh"
    ln -s "/opt/wonderlandengine/bin/WonderlandEditor.sh" \
        "${pkgdir}/usr/bin/WonderlandEditor"
    # lib files
    cp -r "lib" "${pkgdir}/opt/wonderlandengine"
    chmod -R 755 "${pkgdir}/opt/wonderlandengine"
    # share files
    install -dm755 "${pkgdir}/opt/wonderlandengine/share"
    cp -r "share/wonderlandengine" "${pkgdir}/opt/wonderlandengine/share/wonderlandengine"
    chmod -R 755 "${pkgdir}/opt/wonderlandengine/share/wonderlandengine"
    # icons
    install -d -m755 "${pkgdir}/usr/share/icons/hicolor/128x128/apps"
    cp "share/icons/WonderlandEditor.png" \
        "${pkgdir}/usr/share/icons/hicolor/128x128/apps/WonderlandEditor.png"
    # desktop file
    install -D -m644 "share/applications/WonderlandEditor.desktop" \
        "${pkgdir}/usr/share/applications/WonderlandEditor.desktop"
}
