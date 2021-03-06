# `LaTeX-info.md`

This folder stores LaTeX templates among other boilerplate for LaTeX.

## Links

[📝 The Not So Short Introduction to LATEX 2ε](https://gking.harvard.edu/files/lshort2.pdf)

Dark-mode for pdf output:  
[👥 I just discovered...](https://www.reddit.com/r/GradSchool/comments/cmfxjm/i_just_discovered_how_to_make_darkmode_pdfs_in/)  
/r/GradSchool post

How to add `.sty` files:  
[👥 Include _.sty file from a super/subdirectory of main _.tex file](https://stackoverflow.com/a/5994232)  
Stack overflow answer  
[👤 abcd](https://stackoverflow.com/users/3730911/abcd)

Theorem counters:  
[🥞 Setting Counters for Theorems](https://tex.stackexchange.com/a/173353)  
[👤 Gonzalo Medina](https://tex.stackexchange.com/users/3954/gonzalo-medina)

`\newcommand` with optional argument:  
[🥞 LaTeX Optional Arguments](https://stackoverflow.com/a/1812224)  
[👤 miku](https://stackoverflow.com/users/89391/miku)  
[👤 JesseTG](https://stackoverflow.com/users/1089957/jessetg)

`tcolorbox` versus `mdframed`:  
[🥞 What are the relative strong and weak points between tcolorbox and mdframed?](https://tex.stackexchange.com/a/139912)  
[👤 drini](https://tex.stackexchange.com/users/4453/drini)  
[👤 Sean Allred](https://tex.stackexchange.com/users/17423/sean-allred)

Show url in `References`:  
[🥞 url not showing in references](https://tex.stackexchange.com/a/171453`)  
[👤 pst](https://tex.stackexchange.com/users/48251/pst)

---

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
        "-aux-directory=./out-%DOCFILE%",
        "-output-directory=../../Articles",
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
        "-aux-directory=./out-%DOCFILE%",
        "-output-directory=./",
        "%DOC%"
      ]
    }
  ],
  "[latex]": {
    "editor.defaultFormatter": "James-Yu.latex-workshop"
  }
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

since some non-pdf files were still output into the current directory.
