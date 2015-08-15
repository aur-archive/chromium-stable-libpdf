# Contributor: sxe <sxxe@gmx.de> 
pkgname=chromium-stable-libpdf
pkgver=latest
pkgrel=2
pkgdesc="Build in PDF viewer (libpdf plugin) for Chromium stable version"
url="http://wiki.archlinux.org/index.php/Chromium#libpdf.so"
arch=("i686" "x86_64")
license="non-free"
depends=('chromium')

# Get correct version for CARCH
    if [ $CARCH = "i686" ]; then
        libpdf_arch="i386"
    else 
        if [ $CARCH = "x86_64" ]; then
            libpdf_arch="amd64"
        fi
    fi

package() {

    SRC="google-chrome-stable_current_${libpdf_arch}.deb"
    SRC_URI="https://dl-ssl.google.com/linux/direct/${SRC}"

    msg "Downloading..."
        curl -zf ${SRC_URI} -o ${SRC}

    msg "Extracting..."
        ar p ${SRC} data.tar.lzma | tar --lzma -xvf -

    msg "Packaging..."

    cd ${srcdir}
    install -Dm 755 ./opt/google/chrome/libpdf.so \
			${pkgdir}/usr/lib/chromium/libpdf.so
}
