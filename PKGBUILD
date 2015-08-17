# Maintainer: Andy Weidenbaum <archbaum@gmail.com>

pkgname=vim-colors-jellyx-git
pkgver=20140522
pkgrel=1
pkgdesc="A delicious collision of Jellybeans and Xoria256"
arch=('any')
depends=('vim')
makedepends=('git')
groups=('vim-plugins')
url="https://github.com/guns/jellyx.vim"
license=('MIT')
source=(${pkgname%-git}::git+https://github.com/guns/jellyx.vim)
sha256sums=('SKIP')
provides=('vim-colors-jellyx' 'vim-jellyx')
conflicts=('vim-colors-jellyx' 'vim-jellyx')
install=jellyx.install

pkgver() {
  cd ${pkgname%-git}
  git log -1 --format="%cd" --date=short | sed "s|-||g"
}

package() {
  cd ${pkgname%-git}

  msg 'Installing docs...'
  install -Dm 644 README.markdown "$pkgdir/usr/share/doc/vim-colors-jellyx/README.markdown"

  msg 'Installing dirs...'
  install -dm 755 "$pkgdir/usr/share/vim/vimfiles"
  for _dir in colors; do
    cp -dpr --no-preserve=ownership $_dir "$pkgdir/usr/share/vim/vimfiles/$_dir"
  done

  msg 'Cleaning up pkgdir...'
  find "$pkgdir" -type d -name .git -exec rm -r '{}' +
  find "$pkgdir" -type f -name .gitignore -exec rm -r '{}' +
}
