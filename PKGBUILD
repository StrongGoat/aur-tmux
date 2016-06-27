# Maintainer:  WorMzy Tykashi <wormzy.tykashi@gmail.com>
# Contributor: Dmitry Korzhevin <dkorzhevin AT gmail DOT com>
# Contributor: C.Coutinho <kikijump[at]gmail[dot]com>
# Contributor: Grigorios Bouzakis <grbzks[at]gmail[dot]com>
# Contributor: TDY <tdy@gmx.com>

pkgname=tmux-stronggoat
_gitname=tmux
pkgver=2.2.r107.gc07296c
pkgrel=1
pkgdesc="A terminal multiplexer"
url="http://tmux.github.io"
arch=('i686' 'x86_64')
license=('BSD')
depends=('ncurses' 'libevent')
makedepends=('git')
optdepends=('libutempter: Record user sessions to utmp and wtmp files (add to depends array and rebuild to enable)')
#depends+=('libutempter')
provides=('tmux')
conflicts=('tmux')
source=('git+https://github.com/stronggoat/tmux.git#commit=c07296c7da76951aedf868398b43e52d55949534'
        'LICENSE')
md5sums=('SKIP'
         '71601bc37fa44e4395580b321963018e')

pkgver() {
  cd $_gitname
  git describe --long | sed -e 's:\([^-]*-g\):r\1:' -e 's:-:.:g'
}

prepare() {
  cd $_gitname
  ./autogen.sh
}

build() {
  cd $_gitname
  ./configure --prefix=/usr
  make
}

package() {
  cd $_gitname

  make DESTDIR="$pkgdir" install
  install -Dm644 "$srcdir/LICENSE" "$pkgdir/usr/share/licenses/tmux/LICENSE"

  # install example config file
  install -Dm755 example_tmux.conf "$pkgdir/usr/share/tmux/example_tmux.conf"
}
