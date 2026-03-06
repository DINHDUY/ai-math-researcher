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
  Once installed, copy the output files to your Mac and compile:

  cd /path/to/output
  pdflatex fermat_survey
  bibtex fermat_survey
  pdflatex fermat_survey
  pdflatex fermat_survey

  