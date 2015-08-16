# edited by Li Shun <riverscn@gmail.com>
# x86_64 compatible patch by PT<pentie@gmail.com>
# Maintener: Frédérik Paradis <fredy_14@live.fr>

pkgname=jpcap_x86_64_patched
pkgver=0.7
pkgrel=3
pkgdesc="Jpcap is a Java library for capturing and sending network packets."
arch=('i686' 'x86_64')
url="http://netresearch.ics.uci.edu/kfujii/jpcap/doc/index.html"
license=('GPL')
depends=('libpcap' 'java-environment')
source=(http://netresearch.ics.uci.edu/kfujii/jpcap/jpcap-0.7.tar.gz fPIC.patch)
md5sums=('faa3c4be407ce3419cad90150db391a5'
         '80276816e234def98fb20bd59376826b')

build() {
  patch -p0<fPIC.patch || return 1
  cd "$srcdir/jpcap-0.7/src/c" || return 1
  make || return 1
  
  if test "$CARCH" == x86_64; then
    mkdir -p "$pkgdir$JAVA_HOME/jre/lib/amd64" || return 1
    cp libjpcap.so "$pkgdir$JAVA_HOME/jre/lib/amd64" || return 1
  else
    mkdir -p "$pkgdir$JAVA_HOME/jre/lib/i386" || return 1
    cp libjpcap.so "$pkgdir$JAVA_HOME/jre/lib/i386" || return 1
  fi


  mkdir -p "$pkgdir$JAVA_HOME/jre/lib/ext" || return 1
  cp "$srcdir/jpcap-0.7/lib/jpcap.jar" "$pkgdir$JAVA_HOME/jre/lib/ext" || return 1
}

