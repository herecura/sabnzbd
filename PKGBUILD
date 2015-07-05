pkgname=sabnzbd
pkgver=0.7.4
pkgrel=1
pkgdesc="A web-interface based binary newsgrabber with NZB file support"
arch=('any')
url="http://www.sabnzbd.org/"
license=('GPL')
depends=('par2cmdline' 'python2' 'python2-cheetah' 'python2-feedparser' 'python2-yenc' 'python2-pyopenssl' 'unrar' 'unzip' 'sqlite' 'curl')
install=sabnzbd.install
backup=('etc/conf.d/sabnzbd' 'opt/sabnzbd/sabnzbd.ini')
source=("http://downloads.sourceforge.net/sabnzbdplus/SABnzbd-$pkgver-src.tar.gz"
'sabnzbd' 'sabnzbd.init' 'sabnzbd.confd' 'sabnzbd.desktop' 'x-nzb.xml' 'addnzb.sh')

package() {
		mkdir -p ${pkgdir}/opt/
        cp -a ${srcdir}/SABnzbd-$pkgver ${pkgdir}/opt/sabnzbd

        touch ${pkgdir}/opt/sabnzbd/sabnzbd.ini

        find ${pkgdir}/opt/sabnzbd -type d -exec chmod 755 {} \;
        find ${pkgdir}/opt/sabnzbd -type f -exec chmod 644 {} \;

        chmod 755 ${pkgdir}/opt/sabnzbd/SABnzbd.py
        chmod 755 ${pkgdir}/opt/sabnzbd/Sample-PostProc.sh

        install -Dm755 ${srcdir}/sabnzbd ${pkgdir}/usr/bin/sabnzbd
        install -Dm755 ${srcdir}/sabnzbd.init ${pkgdir}/etc/rc.d/sabnzbd
        install -Dm644 ${srcdir}/sabnzbd.confd ${pkgdir}/etc/conf.d/sabnzbd

        install -Dm755 ${srcdir}/sabnzbd.desktop ${pkgdir}/usr/share/applications/sabnzbd.desktop
        install -Dm755 ${srcdir}/addnzb.sh ${pkgdir}/opt/sabnzbd/addnzb.sh
        install -Dm644 ${srcdir}/x-nzb.xml ${pkgdir}/opt/sabnzbd/x-nzb.xml

        # Fix for issues with Python 3
        find ${pkgdir}/opt/sabnzbd -type f -exec sed -i 's/python/python2/g' {} \;
}
sha256sums=('4d23e6135f1cf3599987e68d404e6a6b7e880ace1ade30e54e01e9fa7ee5bf17'
            'f17b424a09f9aa76a57f6dd6640797bc5a0abf6cdf464401c982c8de4842e1f6'
            '8cac283c22b65a199c6bece0a04949d332b163ea6fbfc1411d85700a32cc4f09'
            '8f23c7052a61d65576bd132352bd00a7bff2481472c8b4d84fc6e5c748385652'
            '004ca8611630459cec5825d4f124d164304799b276ae12de29fbfdd2823986f6'
            'f53261d7578c67fb9fd6a639df94cd53604bcf37b9b03a926cb03e5214b496fe'
            'baea3351a40551a63b90b4a4c32719d4c27b5fff596e74e4a91f289964960eb6')
