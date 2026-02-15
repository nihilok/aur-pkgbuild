# Maintainer: nihilok <https://github.com/nihilok>
pkgname=runtool
pkgver=0.3.18
pkgrel=1
pkgdesc="A.K.A. run - the bridge between human and AI tooling"
arch=('x86_64' 'aarch64')
url="https://github.com/nihilok/run"
license=('MIT')
makedepends=('cargo')
source=("$pkgname-$pkgver.tar.gz::https://github.com/nihilok/run/archive/refs/tags/v$pkgver.tar.gz")
sha256sums=('35acf2ebce49dfa1ed1754fd5b8c97822abcce20402310cea2e39be337bca681')

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
