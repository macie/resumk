# resumk

[![License](https://img.shields.io/github/license/macie/resumk)](https://tldrlegal.com/license/mit-license)

**resumk** is a management tool for LaTeX-based resumes. It can:

- interactively create a new resume from the template; inside a company-specific directory
- hot-reload PDF resume during edition.

`resumk` generates PDF preview with [XeTeX](https://en.wikipedia.org/wiki/XeTeX).

## Usage

Calling `resumk` without arguments starts it in a interactive mode. Interactive
mode needs `template-cv.tex` template in current directory:

```sh
$ ls
template-cv.tex
$ resumk
[resumk] Prepare resume inside './ongoing/' from './template-cv.tex' template
[resumk] Enter company name: Acme Corp.
[resumk] Enter position title: Associate Maker
[resumk] Enter keywords (comma separated): something, other thing
[resumk] Prepare 'acme_corp./' dir for company applications
[resumk] Prepare 'acme_corp.-associate_maker-cv.tex' resume
[resumk] Prepare 'acme_corp.-associate_maker.md' with process metadata
[resumk] All files created
[resumk] Prepare 'acme_corp.-associate_maker-cv.pdf' inside '/tmp/resumk.3sCELk/'
  This is XeTeX, Version 3.141592653-2.6-0.999995 (TeX Live 2023/Debian) (preloaded format=xelatex)
  restricted \write18 enabled.
  entering extended mode
  (./ongoing/acme_corp./acme_corp.-associate_maker-cv.tex
  LaTeX2e <2023-11-01> patch level 1
  L3 programming layer <2024-01-22>
  (/usr/share/texlive/texmf-dist/tex/latex/base/article.cls
  Document Class: article 2023/05/17 v1.4n Standard LaTeX document class
  (/usr/share/texlive/texmf-dist/tex/latex/base/size11.clo))
  (/usr/share/texlive/texmf-dist/tex/latex/l3backend/l3backend-xetex.def)
  No file acme_corp.-associate_maker-cv.aux.
  (/usr/share/texlive/texmf-dist/tex/latex/base/ts1cmr.fd) [1]
  (/tmp/resumk.3sCELk/acme_corp.-associate_maker-cv.aux) )
  Output written on /tmp/resumk.3sCELk/acme_corp.-associate_maker-cv.pdf (1 page)
  .
  Transcript written on /tmp/resumk.3sCELk/acme_corp.-associate_maker-cv.log.
[resumk] Open '/tmp/resumk.3sCELk/acme_corp.-associate_maker-cv.pdf' in default PDF viewer
[resumk] Watch 'acme_corp.-associate_maker-cv.tex' for changes...  (CTRL-C to exit)
^C[resumk] Delete '/tmp/resumk.3sCELk/' working dir
```

### Resume template

A template file contains keys substitutes by `resumk`:

- `%%POSITION%%`
- `%%COMPANY%%`
- `%%KEYWORDS%%`.

For example, to add proper PDF metadata, use:

```latex
\usepackage{hyperref}
\hypersetup
{
  pdfauthor={John Smith},
  pdfsubject={Application for %%POSITION%% at %%COMPANY%%},
  pdftitle={John Smith -- Job Application},
  pdfkeywords={
    {%%POSITION%%, CV, résumé, }
    {%%KEYWORDS%%, }
    {%%COMPANY%%, }
    {curriculum vitae, resume}
  }
}
```

## Installation

### Development version

```bash
git clone git@github.com:macie/resumk.sh.git
cd resumk
make install
```

## Development

Use `make`:

- `make` - run checks
- `make test` - run test
- `make check` - perform static code analysis
- `make install` - install in `/usr/local/bin`
- `make dist` - prepare for distributing
- `make clean` - remove distribution artifacts
- `make info` - print system info (useful for debugging).

## License

[MIT](./LICENSE)
