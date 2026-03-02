# Maintainer: nihilok <https://github.com/nihilok>
pkgname=runtool
pkgver=0.3.26
pkgrel=1
pkgdesc="A.K.A. run - the bridge between human and AI tooling"
arch=('x86_64' 'aarch64')
url="https://github.com/nihilok/run"
license=('MIT')
makedepends=('cargo')
source=("$pkgname-$pkgver.tar.gz::https://github.com/nihilok/run/archive/refs/tags/v$pkgver.tar.gz")
sha256sums=('4e135a5298a2e5b323f2755f0e55e343191da07eaf30eccd06da0f65adeda59b')

prepare() {
    cd "run-$pkgver"
    export RUSTUP_TOOLCHAIN=stable
    cargo fetch --locked --target "$(rustc -vV | sed -n 's/host: //p')"
}

build() {
    cd "run-$pkgver"
    export RUSTUP_TOOLCHAIN=stable
    export CARGO_TARGET_DIR=target
    cargo build --frozen --release --package run
}

package() {
    cd "run-$pkgver"
    install -Dm0755 "target/release/run" "$pkgdir/usr/bin/run"
    install -Dm0644 "LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
