# Maintainer: Agustin Ferrario "py_crash < agustin dot ferrario at hotmail dot com dot ar >
# Contributor: Luis von Bernus <PaterSiul@gmail.com>
# Contributors: L42y, aeosynth, Dan Serban, Kalipath

pkgname=firefox-aurora
pkgver=21.0a2
pkgrel=4
pkgdesc="Firefox Aurora channel - Nightly build"
url=http://www.mozilla.org/en_US/firefox/aurora/
arch=(i686 x86_64)
license=(MPL GPL LGPL)
depends=('gtk2' 'libxt' 'startup-notification' 'mime-types' 'dbus-glib' 'alsa-lib' 'dbus-glib' 'libnotify' 'desktop-file-utils' 'hicolor-icon-theme' 'libvpx' 'libevent' 'nss>=3.14.1' 'hunspell')
optdepends=()
makedepends=('wget')
provides=(firefox-aurora)
conflicts=(firefox-aurora)
install=$pkgname.install
_baseurl=http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-aurora
_filename=firefox-${pkgver}.en-US.linux-${CARCH}
source=(firefox-aurora.desktop
	firefox-aurora-safe.desktop
	"${_baseurl}/${_filename}.tar.bz2")
_md5=$(wget -qO- ${_baseurl}/${_filename}.checksums | awk -F' ' '$2 == "md5" && $4 == "'"${_filename}.tar.bz2"'" { print $1 } ')
md5sums=('663176661ce817e40b4217c5e107df42'
         '1fbf95734ceb475ac2ac6ab085fc1961'
         ${_md5})
package()
{
  mkdir -p "${pkgdir}"/{usr/{bin,share/{applications,pixmaps}},opt}
  mv firefox firefox-aurora
  mv firefox-aurora "${pkgdir}"/opt/
  ln -s /opt/firefox-aurora/firefox "${pkgdir}"/usr/bin/firefox-aurora
  install -m644 "${startdir}"/{firefox-aurora.desktop,firefox-aurora-safe.desktop} "${pkgdir}"/usr/share/applications/
  install -m644 "${pkgdir}"/opt/firefox-aurora/browser/icons/mozicon128.png "${pkgdir}"/usr/share/pixmaps/firefox-aurora-icon.png
}

