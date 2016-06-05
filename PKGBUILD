pkgname=sabnzbd
_pkgname=SABnzbd
pkgver=1.0.3
pkgrel=1
pkgdesc="A web-interface based binary newsgrabber with NZB file support"
url="http://www.sabnzbd.org"
arch=("any")
license=("GPL")
depends=(
	"par2cmdline"
	"python2-cheetah"
	"python2-yenc"
	"sqlite"
	"unrar"
	"unzip"
    'desktop-file-utils'
    'hicolor-icon-theme'
    'shared-mime-info'
)
optdepends=(
	"xdg-utils: registration of .nzb files"
	"curl: if you want to add ExecStop" 
	"python2-pyopenssl: https support"
	"python2-feedparser: rss support"
)
install="${pkgname}.install"
backup=("opt/${pkgname}/${pkgname}.ini")
source=(
	"http://downloads.sourceforge.net/sabnzbdplus/${_pkgname}-${pkgver}-src.tar.gz"
	"${pkgname}"
	"${pkgname}.desktop"
	"addnzb.sh"
	"nzb-2.png"
	"sab2_64.png"
	"x-nzb.xml"
	"${pkgname}.service"
)
sha256sums=('cf87d3f17fc03e8b3a4b3010261115c2ad7e2f773b5ede95a80025b340dbbd35'
            '82630edfc767a383843ffaae9d716e99010dad9e93bdee08d541faa74e694a65'
            '6214a92f775888133a8f87ec69e4d0d2ecc9fafbe61387778767000e4db3ea8f'
            'baea3351a40551a63b90b4a4c32719d4c27b5fff596e74e4a91f289964960eb6'
            '7fec4494a04ffd6a94644c8ef499ec1c92998a613b1fde5c3a46f38c53dfbc43'
            '099d625d6efc9e69e7c6a2833221928fb19e9e356e3aa8341c36ffdc281e567d'
            'f53261d7578c67fb9fd6a639df94cd53604bcf37b9b03a926cb03e5214b496fe'
            'f3ab799b24ffab84fea95214b63ba548be2787a47cd802a05967361f1efb43d6')

package() {
	mkdir -p "${pkgdir}/opt/${pkgname}"
	touch "${pkgdir}/opt/${pkgname}/.${pkgname}.ini"
	cp -rv "${srcdir}/${_pkgname}-${pkgver}/"* "${pkgdir}/opt/${pkgname}"

	# make sure it uses python2
	find "${pkgdir}/opt/${pkgname}" -type f -exec sed -i 's/python/python2/g' {} \;
	find "${pkgdir}/opt/${pkgname}" -type d -exec chmod 755 {} \;
	find "${pkgdir}/opt/${pkgname}" -type f -exec chmod 644 {} \;

	chmod 755 "${pkgdir}/opt/${pkgname}/${_pkgname}.py"
	#chmod 755 "${pkgdir}/opt/${pkgname}/Sample-PostProc.sh"

	install -Dm755 "${srcdir}/${pkgname}" \
		"${pkgdir}/usr/bin/${pkgname}"
	install -Dm644 "${srcdir}/${pkgname}.service" \
		"${pkgdir}/usr/lib/systemd/system/${pkgname}.service"
	install -Dm755 "${srcdir}/${pkgname}.desktop" \
		"${pkgdir}/usr/share/applications/${pkgname}.desktop"
	install -Dm755 "${srcdir}/addnzb.sh" \
		"${pkgdir}/opt/${pkgname}/addnzb.sh"
	install -Dm644 "${srcdir}/nzb-2.png" \
		"${pkgdir}/opt/${pkgname}/nzb-2.png"
	install -Dm644 "${srcdir}/sab2_64.png" \
		"${pkgdir}/opt/${pkgname}/sab2_64.png"
	install -Dm770 "${srcdir}/x-nzb.xml" \
		"${pkgdir}/opt/${pkgname}/x-nzb.xml"
}

