pkgname=sabnzbd
_pkgname=SABnzbd
pkgver=2.0.0
pkgrel=2
pkgdesc="A web-interface based binary newsgrabber with NZB file support"
url="http://www.sabnzbd.org"
arch=("any")
license=("GPL")
depends=(
	"par2cmdline"
	"python2-cheetah"
	"python2-sabyenc"
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
    "https://github.com/${pkgname}/${pkgname}/releases/download/${pkgver}/${_pkgname}-${pkgver}-src.tar.gz"
	"${pkgname}"
	"${pkgname}.desktop"
	"addnzb.sh"
	"nzb-2.png"
	"sab2_64.png"
	"x-nzb.xml"
	"${pkgname}.service"
)
sha512sums=('e32f869f84622ee21b5c373f91fe1d2ae867e49f8d764d47d341d61bcc1641e4c6d4bc41537b0e141d1016776b5de694e696c1fa62ac0dd4771b3cd6e8f5e32a'
            '98bcc1bc6137208a9c44749e76f8d5eccc7a77c4b3bb4066c868f11f50cca4485ee12830752cc9ec45b2a806d7f98707a09feaee145a94bd61a7c62a9113845a'
            '3c787adf220447b30e3af30c9abf60f484b56c5fd12a4335c2225f7b533ee386e88d1aba1c41514f6f687aa5554782c8e27740d1d2071260956c10e412b5aba0'
            'dc35291f22b126fa9739148f98570a5a828ba2f52e5da0c9ba04ff9b0641cba95774619a83e26bc12b2527b77b7c3a7768ac6ca176bd6c3c547960f842e913ba'
            'dd59c27b1d52addee8c3e8b9a8f6e5c89afba169ed6d17cf811e27f998509d14c64dad96ea2d28501704281acb4ee393dbe314a921f73da377fc599eb9ec7bdd'
            'c135278e254611e1ad6e34ec2d6f207e2299dbf3c3ce3ddef2e7bbfe83129d29b51ad6041a90559409d1734d7092ffe7a6c8f78c3d1372b6d2d58bff9c553a84'
            'bd0345ca5f9f826e9686818a703ad88f22133a50a308af2c3acf8c370479bdcc38a9ff639b2046a3281d4d4bce443b11e39a1b47073ce0ff7c5fc71abbe2ec77'
            '87e6a07774e958c49ca62eca34b045521937fcfa9c11320996dadb280e4637cdf4bca10f3bc2af41fdde075f37fba0440b357946efc14bc5b1e73c9b53d13d1e')

package() {
	mkdir -p "${pkgdir}/opt/${pkgname}"
	touch "${pkgdir}/opt/${pkgname}/.${pkgname}.ini"
	cp -rv "${srcdir}/${_pkgname}-${pkgver}/"* "${pkgdir}/opt/${pkgname}"

	# make sure it uses python2
	find "${pkgdir}/opt/${pkgname}" -type f -exec sed -i 's/python/python2/g' {} \;
	find "${pkgdir}/opt/${pkgname}" -type d -exec chmod 755 {} \;
	find "${pkgdir}/opt/${pkgname}" -type f -exec chmod 644 {} \;

	chmod 755 "${pkgdir}/opt/${pkgname}/${_pkgname}.py"

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

