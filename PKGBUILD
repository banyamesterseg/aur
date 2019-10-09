# Maintainer: Gaetan Bisson <aldum@artixlinux.org>

pkgname=minetest-banyamesterseg
_pkgname=minetest
pkgver=20191010.630c1f5f
pkgrel=1
pkgdesc='Voxel game engine and Infiniminer/Minecraft-inspired game'
url='http://www.minetest.net/'
license=('LGPL2.1' 'CCPL:by-sa')
arch=('i686' 'x86_64')
makedepends=('git' 'cmake')
depends=('bzip2' 'freetype2' 'irrlicht' 'jsoncpp' 'leveldb' 'libjpeg'
         'libpng' 'libvorbis' 'luajit' 'mesa' 'openal' 'sqlite' 'hiredis')
source=('git://github.com/banyamesterseg/minetest.git#branch=banyamesterseg'
        'git://github.com/minetest/minetest_game.git')
sha256sums=('SKIP' 'SKIP')

conflicts=("${_pkgname}"{,-common,-server})
provides=("${_pkgname}"{,-common,-server})
install=install

pkgver() {
	cd "${srcdir}/${_pkgname}"
	git log -1 --format='%cd.%h' --date=short | tr -d -
}

prepare() {
	cd "${srcdir}"
}

build() {
	cd "${srcdir}/${_pkgname}"
	cmake . \
		-DCMAKE_BUILD_TYPE=Release \
		-DCMAKE_INSTALL_PREFIX=/usr \
		-DENABLE_GETTEXT=TRUE \
		-DRUN_IN_PLACE=FALSE \
		-DBUILD_SERVER=TRUE \

	make
}

package() {
	cd "${srcdir}/${_pkgname}"
	make DESTDIR="${pkgdir}" install
}
