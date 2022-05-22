#!/bin/bash

# Created from the original PKGBUILD by Caleb Maclennan <caleb@alerque.com> and Guillaume Horel <guillaume.horel@gmail.com>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors

# Maintainer: Ross Clark <https://github.com/Archiv8/python-fontparts/discussions>
# Contributor: Ross Clark <https://github.com/Archiv8/python-fontparts/discussions>


_langname="python"
_relname="fontParts"
_pacname="fontparts"

pkgname="${_langname}-${_pacname}"
pkgver=0.10.5
pkgrel=1
pkgdesc="An API for interacting with the parts of fonts during the font development proce"
arch=(any)
url="https://github.com/robotools/fontparts"
license=(
  "MIT"
)
depends=(
  "python"
  "python-booleanoperations"
  "python-defcon"
  "python-fontmath"
  "python-fontpens" # for defcon[pens]
  "python-fonttools"
  "python-fs"   # for fonttools[ufo]
  "python-lxml" # for fonttools[lxml]
  "python-unicodedata2"
)
makedepends=(
  "python-build"
  "python-installer"
  "python-setuptools-scm"
  "python-wheel"
)
_zipname="${_relname}-${pkgver}"
source=(
  "https://files.pythonhosted.org/packages/source/${_relname::1}/${_relname}/${_zipname}.zip"
)
sha512sums=(
  "c4d1f1a48f3376198c73127b6ba5937fd0966c3a168a10a8c87f7b86a3cfb3b1a3665de752e2b6907464f81897cc92a0fa3fbca2d81e9649cd5e62203c0b4e68"
)

build() {

  cd "${_zipname}"

  python -m build -wn
}

check() {

  cd "${_zipname}/Lib"

  PYTHONPATH=. python "${_relname}/fontshell/test.py"
}

package() {

  cd "$_zipname"

  python -m installer -d "${pkgdir}" dist/*.whl

  install -Dm0644 -t "${pkgdir}/usr/share/licenses/${pkgname}/" LICENSE
}
