# Maintainer: Limao Luo <luolimao+AUR@gmail.com>
# Contributor: sausageandeggs <sausageandeggs@archlinux.us>
# Contributor: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Daniel J Griffiths <ghost1227@archlinux.us>
# Contributor: Roman Kyrylych <Roman.Kyrylych@gmail.com>
# Contributor: William Rea <sillywilly@gmail.com>

pkgname=everygui
pkgver=0.99.b
pkgrel=8
pkgdesc="GTK+ interface for 'everything'"
arch=(any)
url=http://$_pkgname.sourceforge.net
license=(GPL2 LGPL2.1)
depends=(pygtk)
source=(http://downloads.sourceforge.net/$pkgname/$pkgname-$pkgver.tar.gz
    setup.patch)
sha256sums=('0d824ffa35a539e79611eba6224dd7840b8cc024204b5c9935e8ca11b046ff08'
    '75110ecf40eb4eb0f7f40ff3d3260b6c65153d2b92e484d505b44602800fc40c')
sha512sums=('e3d20a07b40e95da93417344f374803e0a4f954147e740be998dfedb79e1b37a19c4da620706958a29d2af0aca88f68dba092106ebcd90c16af951f6b1071359'
    'a7134f17a263156fd84a1a0b95657dfea791f728d8dee1a23e015cdca927d75efc6acba6a88f743392ae15d3ddc9ac20bdbd437fb37f2901dc54a3d7b7c0e400')

prepare() {
    cd $pkgname/
    for i in $(find -name everygui) $(find -name egdesign); do
        sed -i 's:python /usr/src:exec python2 /usr/lib/python2.7/site-packages:' "$i"
    done
    sed -i 's:\r::g' setup.py
    patch -p1 -i ../setup.patch
}

package() {
    cd $pkgname/
    python2 setup.py install --root="$pkgdir" --optimize=1
    chmod 777 "$pkgdir"/usr/share/$pkgname/egconfig
}
