# Contributor: cuihao <cuihao dot leo at gmail dot com>
# Maintainer: Dennis <arch@tossp.com>

_language_selector=0.113
_ttf_arphic_ukai=0.2.20080216.1
_ttf_arphic_uming=0.2.20080216.1
_ttf_wqy_zenhei=0.9.45

pkgname=fontconfig-ubuntu-zh-cn
pkgver=2
pkgrel=5
pkgdesc="Chinese font configs from Ubuntu"
arch=('i686' 'x86_64')
url="http://www.ubuntu.com"
license=('unknown')
depends=('wqy-zenhei' 'ttf-arphic-ukai' 'ttf-arphic-uming' 'fontconfig-ubuntu')
install=fontconfig.install
source=(
  "http://mirrors.163.com/ubuntu/pool/main/l/language-selector/language-selector_${_language_selector}.tar.gz"
  "http://mirrors.163.com/ubuntu/pool/main/t/ttf-arphic-ukai/ttf-arphic-ukai_${_ttf_arphic_ukai}.orig.tar.gz"
  "http://mirrors.163.com/ubuntu/pool/main/t/ttf-arphic-uming/ttf-arphic-uming_${_ttf_arphic_uming}.orig.tar.gz"
  "http://mirrors.163.com/ubuntu/pool/main/t/ttf-wqy-zenhei/ttf-wqy-zenhei_${_ttf_wqy_zenhei}.orig.tar.gz"
  "original.patch"
)
md5sums=('638de6e63aa08ddcb3153c4d692e0676'
         '4d3beb55db000bfedd18c9c7d6e631d8'
         'd219fcaf953f3eb1889399955a00379f'
         '4c6c3f4e902dd5ee0a121e8c41d040bd'
         'c5de97d0b699afc98a50826b9c00f4cf')
#generate with 'makepkg -g'

build(){
  ls
  mkdir -p $pkgdir/etc/fonts/conf.avail/

  cd $srcdir/language-selector-${_language_selector}/fontconfig
  install -Dm0644 30-cjk-aliases.conf $pkgdir/etc/fonts/conf.avail/
  install -Dm0644 69-language-selector-zh-cn.conf $pkgdir/etc/fonts/conf.avail/
  install -Dm0644 99-language-selector-zh.conf $pkgdir/etc/fonts/conf.avail/
  
  cd $srcdir
  for _f in *.conf
  do
    install -Dm0644 $_f $pkgdir/etc/fonts/conf.avail/$_f
  done
  
  cd $srcdir/wqy-zenhei
  for _f in *.conf
  do
    install -Dm0644 $_f $pkgdir/etc/fonts/conf.avail/$_f
  done

  rm $pkgdir/etc/fonts/conf.avail/43-wqy-zenhei-sharp.conf
  cd "$pkgdir/etc/fonts/conf.avail/"
  patch -u  < ../../../../../original.patch
}
