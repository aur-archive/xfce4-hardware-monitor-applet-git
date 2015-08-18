# Maintainer : Maximilien Noal <noal dot maximilien at gmail dot com> [AUR: xcomcmdr]

pkgname=xfce4-hardware-monitor-applet-git
_gitname=xfce4-applet
_prj=hardware-monitor-applet
pkgver=1.4.4.r53.4f7535e
pkgrel=1
pkgdesc="Plugin for the Xfce4 panel that lets you monitor CPU usage, network bandwith, etc."
arch=('i686' 'x86_64')
provides=('xfce4-hardware-monitor-applet')
url=('https://github.com/OmegaPhil/hardware-monitor-applet/tree/xfce4-applet')
depends=('lm_sensors' 'gtkmm' 'libglademm' 'libgnomecanvasmm' 'libgtop' \
        'libxfce4ui' 'xfce4-panel')
makedepends=('intltool' 'git' 'xfce4-dev-tools')
license=('GPL3')
source=("git://github.com/OmegaPhil/hardware-monitor-applet#branch=${_gitname}")
md5sums=('SKIP')

pkgver() {
  cd "${srcdir}/${_prj}"
  _release=$(grep Release ChangeLog | head -n 1 | awk '{print $2}')
  printf "${_release}.r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  cd "${srcdir}/${_prj}"
  ./autogen.sh
  ./configure --prefix=/usr
  make
}

package() {
  cd "$srcdir/${_prj}"
  make DESTDIR=${pkgdir} install
}
