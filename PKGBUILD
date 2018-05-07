# Contributor: Olivier Mehani <shtrom-aur@ssji.net>
# Contributor: florianbw <florian.bw@gmail.com>
# vim:set ts=2 sw=2 et:

pkgname=latex-template-springer
pkgver=201309
pkgrel=1
pkgdesc="Springer templates for LNCS proceedings (llncs), monographs (svmono), multiauthor volumes (svmult), journals (svjour3), and other lecture notes (svmultln)"
arch=('any')
url="https://www.springer.com/gp/computer-science/lncs/conference-proceedings-guidelines"
license=('')
groups=()
depends=('texlive-latex3')
makedepends=('unzip')
optdepends=()
provides=(latex-template-lncs)
conflicts=(latex-template-lncs)
replaces=(latex-template-lncs)
backup=()
options=()
install=texlive.install
source=(ftp://ftp.springernature.com/cs-proceeding/llncs/llncs2e.zip
https://resource-cms.springernature.com/springer-cms/rest/v1/content/20568/data/v1
https://resource-cms.springernature.com/springer-cms/rest/v1/content/20566/data/v3
https://static.springer.com/sgw/documents/468198/application/zip/LaTeX_DL_468198_220118.zip)

package() {
  for _SVJOUR3 in readme.txt svjour3.cls usrguid3.pdf svglov3.clo template.tex; do
    install -m 0644 -D ${srcdir}/${_SVJOUR3} ${pkgdir}/usr/share/texmf-dist/tex/latex/svjour3/${_SVJOUR3}
  done

  for _SVMONO in instruct.pdf quickstart.pdf refguide.pdf styles/* templates/*; do
    [[ ${_SVMONO} == *"/*" ]] && install -m 755 -d ${pkgdir}/usr/share/texmf-dist/tex/latex/svmono/${_SVMONO#/*}
    install -m 0644 -D ${srcdir}/${_SVMONO} ${pkgdir}/usr/share/texmf-dist/tex/latex/svmono/${_SVMONO%\*}
  done

  for _SVMULT in instruct.pdf quickstart.pdf refguide.pdf styles/* templates/*; do
    [[ ${_SVMULT} == *"/*" ]] && install -m 755 -d ${pkgdir}/usr/share/texmf-dist/tex/latex/svmult/${_SVMULT#/*}
    install -m 0644 -D ${srcdir}/${_SVMULT} ${pkgdir}/usr/share/texmf-dist/tex/latex/svmult/${_SVMULT%\*}
  done

  for _LLNCS in readme.txt llncs.cls llncsdoc.pdf; do
    install -m 0644 -D ${srcdir}/${_LLNCS} ${pkgdir}/usr/share/texmf-dist/tex/latex/llncs/${_LLNCS}
  done

  install -m 0644 -D ${srcdir}/spphys.bst ${pkgdir}/usr/share/texmf-dist/bibtex/bst/springer/spphys.bst
  install -m 0644 -D ${srcdir}/splncs04.bst ${pkgdir}/usr/share/texmf-dist/bibtex/bst/springer/splncs04.bst
  find ${pkgdir}/usr/share/texmf-dist/tex/latex/ -name \*.bst -exec mv {} ${pkgdir}/usr/share/texmf-dist/bibtex/bst/springer/ \;
  # XXX: BSTs have disappeared from the latest version of svmono... Go figure...
  #mv ${pkgdir}/usr/share/texmf-dist/tex/latex/svmono/*.bst \
  # ${pkgdir}/usr/share/texmf-dist/bibtex/bst/springer/
}

md5sums=('SKIP'
         'SKIP'
         'SKIP'
         'SKIP')
