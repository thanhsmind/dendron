---
alias:
- BibLaTeX
type: programing
---
# LaTeX Biblatex

Use the package via:

`\usepackage[backend=biber, style=authoryear-icomp]{biblatex}`  
`\addbibresource{<file path to .bib file>}`

To print our your bibliography:

`\printbibliography`

`\textcite{<ref>}` will add a reference like _Mould [1]_ but 'Mould' would be the name of the ref you passed in and it has that number but adding `style=authoryear-icomp` to the biblatex package optional arg will change it to _Mould (2003)_ with no brackets and numbers

`\parencite{<ref>}` is what I typically like and use and appears like _(Mould 2003)_

## Documentation

-   [OverleafOnBiber](https://www.overleaf.com/learn/latex/Bibliography_management_with_bibtex)