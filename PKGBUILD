# Maintainer: nihilok <https://github.com/nihilok>
pkgname=runtool
pkgver=0.4.2
pkgrel=1
pkgdesc="A.K.A. run - the bridge between human and AI tooling"
arch=('x86_64' 'aarch64')
url="https://github.com/nihilok/run"
license=('MIT')
makedepends=('cargo')
source=("$pkgname-$pkgver.tar.gz::https://github.com/nihilok/run/archive/refs/tags/v$pkgver.tar.gz")
sha256sums=('b224f18f02ab239e7281ee9c4e0dc4257afb0938983e0b1f4d37935b3b47c740')

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
