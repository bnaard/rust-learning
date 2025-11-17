[![Build cheatsheet](https://github.com/bnaard/rust-learning/actions/workflows/build-cheatsheet.yml/badge.svg)](https://github.com/bnaard/rust-learning/actions/workflows/build-cheatsheet.yml)

Rust cheatsheet sources and build instructions

Build status: click the badge above to view the latest workflow runs and artifacts.

This repository contains the source files for a printable Rust cheatsheet (LaTeX source in `cheatsheet/`).

**Build prerequisites**

- A working LaTeX installation. For the easiest experience install a full TeX Live distribution (recommended):

	```bash
	# Debian / Ubuntu (recommended: texlive-full)
	sudo apt update
	sudo apt install -y texlive-full latexmk inkscape python3-pygments
	```

	If you prefer a smaller install, ensure you have these packages (or the equivalents) installed: `texlive-latex-recommended`, `texlive-latex-extra`, `texlive-fonts-recommended`, `texlive-pictures`, `texlive-publishers`, `latexmk`, and `inkscape` plus `python3-pygments` for the `minted` package.

- The LaTeX source uses the `minted` package (requires Pygments) and the `svg` package (calls `inkscape`), so the LaTeX runs must allow shell escapes.

**Build (recommended)**

From the repository root run:

```bash
cd cheatsheet
# recommended: latexmk drives multiple runs and cleanup, with pdflatex and shell-escape enabled
latexmk -pdf -pdflatex="pdflatex -interaction=nonstopmode -shell-escape %O %S" cheatsheet.tex
```

**Alternative (simple) build**

If you don't have `latexmk`, run `pdflatex` twice (the `-shell-escape` flag is required for `minted` and SVG conversion):

```bash
pdflatex -interaction=nonstopmode -shell-escape cheatsheet/cheatsheet.tex
pdflatex -interaction=nonstopmode -shell-escape cheatsheet/cheatsheet.tex
```

After a successful build the PDF will be produced alongside the TeX source (e.g. `cheatsheet/cheatsheet.pdf`).

**Troubleshooting**

- If LaTeX fails with missing package errors, install the appropriate TeX Live collections or use `texlive-full`.
- If you see errors from `minted` about Pygments, ensure `python3-pygments` (or `pip install Pygments`) is available and that you compile with `-shell-escape`.
- If `svg` conversion fails, make sure `inkscape` is installed and on the `PATH`.
- Font-related warnings/errors can usually be resolved by installing additional TeX font packages or using a full TeX Live install.

**Notes**

- The `cheatsheet/cheatsheet.tex` file is released under the MIT License (see the header in the file).
- Ignore the `course/` directory for building the cheatsheet.

If you want, I can attempt to compile the cheatsheet PDF here (the dev container must have the LaTeX toolchain installed). If you'd like that, tell me and I will run the build and report results.


