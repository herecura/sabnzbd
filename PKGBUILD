# Maintainer: Donald Webster <fryfrog@gmail.com>

pkgname=sabnzbd
pkgver=3.0.0
pkgrel=1
pkgdesc='A web-interface based binary newsgrabber with NZB file support'
url='http://www.sabnzbd.org'
arch=('any')
license=('GPL')
depends=(
  'curl'
  'par2cmdline'
  'python'
  'python-six'
  'python-cryptography'
  'python-feedparser'
  'python-configobj'
  'python-cherrypy'
  'python-portend'
  'python-pyopenssl'
  'python-chardet'
  'python-notify2'
  'python-cheetah3'
  'python-sabyenc'
  'sqlite'
  'unrar'
  'unzip'
)

optdepends=(
  'python-pygobject: tray icon'
  'p7zip: for .7z support'
)

backup=('var/lib/sabnzbd/sabnzbd.ini')

install='sabnzbd.install'

source=(
  "https://github.com/sabnzbd/sabnzbd/releases/download/${pkgver}/SABnzbd-${pkgver}-src.tar.gz"
  'sabnzbd.service'
  'sabnzbd@.service'
  'sabnzbd.sysusers'
  'sabnzbd.tmpfiles'
)
        
sha256sums=('2fea94378de55ff6f182c404f6afbe06f8c272855efc344d6354e433272ef24d'
            'c1bcdb5ce7787aab5ab4f07508c1451441f42df0ec7be85a5dedda0a5ee70014'
            '49c8730889c67bcb76675a5c6ac186e719ac6de957525ec72972b7de53432e47'
            '525f294372963fde09db08b0368c80078a16d4cefcb34f8179706336709afdf7'
            '3a3c292020cca0251478c70a6499afa64aeca3dfcb6d5e32f6e21d5d4d94fa81')

package() {
  mkdir -p "${pkgdir}/usr/lib/sabnzbd"
  cp -r "${srcdir}/SABnzbd-${pkgver}/"* "${pkgdir}/usr/lib/sabnzbd"

  find "${pkgdir}/usr/lib/sabnzbd" -type d -exec chmod 755 {} \;
  find "${pkgdir}/usr/lib/sabnzbd" -type f -exec chmod 644 {} \;
  chmod 755 "${pkgdir}/usr/lib/sabnzbd/SABnzbd.py"

  install -D -m 644 "${srcdir}/sabnzbd.service" "${pkgdir}/usr/lib/systemd/system/sabnzbd.service"
  install -D -m 644 "${srcdir}/sabnzbd@.service" "${pkgdir}/usr/lib/systemd/system/sabnzbd@.service"
  install -D -m 644 "${srcdir}/sabnzbd.sysusers" "${pkgdir}/usr/lib/sysusers.d/sabnzbd.conf"
  install -D -m 644 "${srcdir}/sabnzbd.tmpfiles" "${pkgdir}/usr/lib/tmpfiles.d/sabnzbd.conf"
}
