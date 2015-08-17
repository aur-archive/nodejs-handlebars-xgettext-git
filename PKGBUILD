# Maintainer: Andy Weidenbaum <archbaum@gmail.com>

pkgname=nodejs-handlebars-xgettext-git
pkgver=20130917
pkgrel=1
pkgdesc="Extract translatable strings from Handlebars templates"
arch=('any')
depends=('nodejs')
makedepends=('git' 'npm')
url="https://github.com/vialink/handlebars-xgettext"
license=('MIT')
source=(${pkgname%-git}::git+https://github.com/vialink/handlebars-xgettext)
sha256sums=('SKIP')
provides=('nodejs-handlebars-xgettext')
conflicts=('nodejs-handlebars-xgettext')

pkgver() {
  cd ${pkgname%-git}
  git log -1 --format="%cd" --date=short | sed "s|-||g"
}

package() {
  local _npmdir="$pkgdir/usr/lib/node_modules/"
  mkdir -p $_npmdir
  cd $_npmdir
  npm install --python=python2 --user root -g --prefix "$pkgdir/usr" vialink/handlebars-xgettext

  msg 'Cleaning up pkgdir...'
  find "$pkgdir" -type d -name .git -exec rm -r '{}' +
  find "$pkgdir" -type f -name .gitignore -exec rm -r '{}' +
}
