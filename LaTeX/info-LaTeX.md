# README.md

This folder stores LaTeX templates among other boilerplate for LaTeX.

## Links

[📝 The Not So Short Introduction to LATEX 2ε](https://gking.harvard.edu/files/lshort2.pdf)

## LaTeX Workshop config

[📝 LaTex Workshop wiki](https://github.com/James-Yu/LaTeX-Workshop/wiki/)

### Disable live reload

Go to `settings.json`, e.g. on Windows by hitting

```
crtl + shift + p
```

and selecting

![`settings.json`](../Images/settings-json.png)

Add the following line:

```
"latex-workshop.latex.autoBuild.run": "never"
```

Source: thie stack overflow [answer](https://stackoverflow.com/a/55912235).

### Change output directory `aux` and `pdf` files

See the LaTeX workshop [issue](https://github.com/James-Yu/LaTeX-Workshop/issues/548). For my own usecase on a Windows machine, I added

```
"latex-workshop.latex.recipes": [
    {
      "name": "latexmk",
      "tools": ["latexmk"]
    }
  ],
  "latex-workshop.latex.tools": [
    {
      "name": "latexmk",
      "command": "latexmk",
      "args": [
        "-synctex=1",
        "-interaction=nonstopmode",
        "-file-line-error",
        "-pdf",
        "-aux-directory=out",
        "-output-directory=./",
        "%DOC%"
      ]
    },
    {
      "name": "pdflatex",
      "command": "pdflatex",
      "args": [
        "-synctex=1",
        "-interaction=nonstopmode",
        "-file-line-error",
        "-aux-directory=out",
        "-output-directory=./",
        "%DOC%"
      ]
    }
  ]
```

to `settings.json`. I also added a `.gitignore` with

```
# LaTeX extra files (e.g. aux)
*.fls
*.synctex.gz
*.aux
*.log
*.fdb_latexmk
```

since some non-pdf files were still output into the current director.
