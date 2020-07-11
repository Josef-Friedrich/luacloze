# Description

EN: `cloze` is a LuaLaTeX/LaTeX package to generate cloze. It uses the
capabilities of the modern TeX engine LuaTex.

DE: `cloze` ist a LuaLaTeX/LaTeX-Paket zum Erstellen von Lückentexten.
Es nutzt die Möglichkeiten der modernen TeX-Engine LuaTeX.

# License

Copyright (C) 2015-2020 by Josef Friedrich <josef@friedrich.rocks>
------------------------------------------------------------------------
This work may be distributed and/or modified under the conditions of
the LaTeX Project Public License, either version 1.3 of this license
or (at your option) any later version.  The latest version of this
license is in:

  http://www.latex-project.org/lppl.txt

and version 1.3 or later is part of all distributions of LaTeX
version 2005/12/01 or later.

# CTAN

Since July 2015 the cloze package is included in the Comprehensive TeX
Archive Network (CTAN).

* TeX archive: http://mirror.ctan.org/tex-archive/macros/luatex/generic/cloze
* Package page: https://www.ctan.org/pkg/cloze

# Distributions

* MiKTeX: https://miktex.org/packages/cloze
* TeX Live:
  * run files:
    * [cloze.lua](https://tug.org/svn/texlive/trunk/Master/texmf-dist/scripts/cloze/cloze.lua)
    * [cloze.sty](https://tug.org/svn/texlive/trunk/Master/texmf-dist/tex/luatex/cloze/cloze.sty)
    * [cloze.tex](https://tug.org/svn/texlive/trunk/Master/texmf-dist/tex/luatex/cloze/cloze.tex)
  * doc files:
    * [cloze.pdf)](https://tug.org/svn/texlive/trunk/Master/texmf-dist/doc/luatex/cloze/cloze.pdf)
    * [README.md](https://tug.org/svn/texlive/trunk/Master/texmf-dist/doc/luatex/cloze/README.md)

# Repository

https://github.com/Josef-Friedrich/cloze

## Files

* `cloze.dtx`:
  Contains the `cloze.tex` (Plain (Lua)TeX macros) and the `cloze.sty`
  ((Lua)LaTex package). Never edit the files `cloze.tex` and `cloze.sty`
  directly. They are autogenerated.
* `cloze.ins`: Run `luatex cloze.ins` to extract the files embeded into
  `cloze.dtx`.
* `cloze.lua`: The Lua code of the package.
* `documentation.tex`: The LaTeX code to generate the documentation
  `cloze.pdf` from.

# Documentation

* [User documentation as a PDF](http://mirror.ctan.org/tex-archive/macros/luatex/generic/cloze/cloze.pdf)
* [API documentation of the Lua code](https://josef-friedrich.github.io/cloze)

# Installation

## TeX Live

    tlmgr install cloze

## Manually

    git clone git@github.com:Josef-Friedrich/cloze.git
    cd cloze

### Using make (assumes your TeX environment takes `$HOME/texmf` into account)

    make install

### By hand

    mkdir -p $HOME/texmf/tex/luatex/cloze
    cp -f cloze.tex $HOME/texmf/tex/luatex/cloze
    cp -f cloze.sty $HOME/texmf/tex/luatex/cloze
    cp -f cloze.lua $HOME/texmf/tex/luatex/cloze

## Compile the documentation:

    lualatex --shell-escape documentation.tex
    makeindex -s gglo.ist -o documentation.gls documentation.glo
    makeindex -s gind.ist -o documentation.ind documentation.idx
    lualatex --shell-escape documentation.tex
    mv documentation.pdf cloze.pdf
    mkdir -p $HOME/texmf/doc/luatex/cloze
    cp -f cloze.pdf $HOME/texmf/doc/luatex/cloze

# Development

First delete the stable version installed by TeX Live. Because the
package `cloze` belongs to the collection `collection-latexextra`, the
option  `--force` must be used to delete the package.

    tlmgr remove --force cloze

## Deploying a new version

Update the version number in the file `cloze.dtx` on this locations:

### In the markup for the file `cloze.sty` (approximately at the line number 30)

    %<*package>
      [2020/05/20 v1.4 Package to typeset cloze worksheets or cloze tests]
    %<*package>

Add a changes entry (approximately at the line 90):

```latex
\changes{v1.4}{2020/05/20}{...}
```

### In the package documentation `documentation.tex` (approximately at the line number 125)

```latex
\date{v1.6~from 2020/06/30}
```

### In the markup for the file `cloze.lua` (approximately at the line number 1900)

```lua
if not modules then modules = { } end modules ['cloze'] = {
  version   = '1.4'
}
```

### Update the copyright year:

```
sed -i 's/(C) 2015-2020/(C) 2015-2021/g' cloze.ins
sed -i 's/(C) 2015-2020/(C) 2015-2021/g' cloze.dtx
```

### Command line tasks:

```
git tag v1.4
make
make ctan
```
