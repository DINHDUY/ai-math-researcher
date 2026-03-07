 Option A: MacTeX (Full — Recommended)

  brew install --cask mactex

  This installs the complete TeX Live distribution (~4GB). After install, restart your terminal, then:

  eval "$(/usr/libexec/path_helper)"
  pdflatex --version

  Option B: BasicTeX (Lightweight — ~100MB)

  brew install --cask basictex                                                                                    
  Then install the packages the manuscript needs:                                                                 
  eval "$(/usr/libexec/path_helper)"
  sudo tlmgr update --self
  sudo tlmgr install amsmath amscls amsthm mathtools booktabs hyperref cleveref
  
  ---
  Once installed, copy the output files to your Mac and compile.

  Choose the sequence based on how the bibliography is managed:

  If the manuscript uses an inline `thebibliography` environment (no external .bib file), run:

  cd /path/to/output
  pdflatex fermat_carmichael
  pdflatex fermat_carmichael
  pdflatex fermat_carmichael

  If the manuscript uses `\bibliography{...}` with an external .bib file, run the full BibTeX sequence:

  cd /path/to/output
  pdflatex fermat_carmichael
  bibtex fermat_carmichael
  pdflatex fermat_carmichael
  pdflatex fermat_carmichael

  fermat_carmichael.tex uses an inline `thebibliography` environment, so only the pdflatex-only
  sequence is required for that manuscript.

  