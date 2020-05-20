# Maintainer: Colin Adler <colin@coder.com>
# Maintainer: Anmol Sethi <anmol@coder.com>

pkgname=code-server
pkgver=3.3.1
pkgrel=2
pkgdesc="VS Code in the browser"
arch=("x86_64" "aarch64")
url="https://github.com/cdr/code-server"
license=(MIT)
depends=(glibc)
source=(
  "$pkgname-$pkgver.service::https://raw.githubusercontent.com/cdr/code-server/v$pkgver/ci/build/code-server.service"
)
release_name="code-server-${pkgver}-linux"
source_x86_64=(
  "${url}/releases/download/v$pkgver/$release_name-amd64.tar.gz"
)
source_aarch64=(
  "${url}/releases/download/v$pkgver/$release_name-arm64.tar.gz"
)
sha512sums=(
  "7040df09c7404a56dbbb32e09d04ead3b622773520feae19c6710656cef46ca5d79b1972bfebb931e309e495d041b9938cd6a51c39fc0f8f6133dfe711be9280"
)
sha512sums_x86_64=(
  "54447ee354f8e083d07785d23839fd37dca86041059f812532f00bd081ed55fa8780802a34ebcaa6270a16378f38e0c1362c425b43d7692324b341fba0ccec0e"
)
sha512sums_aarch64=(
  "3ceef9fd3c05a3195b2e6cef4529ea7da4fa934f0a0ce962019955df296600395d1cba4ad71ff1f7a52011ea17cedaa9a00d34d1760edd253dbbaf272d34bc72"
)

package() {
  if [[ $(uname -m) == x86_64 ]]; then
    release_name+=-amd64
  else
    release_name+=-arm64
  fi

  mkdir -p "$pkgdir/usr/lib"
  cp -a "$release_name" "$pkgdir/usr/lib/$pkgname"

  mkdir -p "$pkgdir/usr/bin"
  ln -s "/usr/lib/$pkgname/bin/$pkgname" "$pkgdir/usr/bin/$pkgname"

  mkdir -p "$pkgdir/usr/lib/systemd/user"
  cp -a "$pkgname-$pkgver.service" "$pkgdir/usr/lib/systemd/user/$pkgname.service"

  mkdir -p "$pkgdir/usr/share/licenses"
  cp -a "$release_name/LICENSE.txt" "$pkgdir/usr/share/licenses/$pkgname"
}
