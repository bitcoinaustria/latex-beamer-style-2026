# Bitcoin Austria — Beamer Style (2026)

A LaTeX **Beamer** theme implementing the Bitcoin Austria 2026 brand, packaged
for reuse across presentations (consumed as a **git submodule**).

![brand](https://img.shields.io/badge/font-Blinker-E3000F) ![license](https://img.shields.io/badge/code-Apache--2.0-222222) ![font-license](https://img.shields.io/badge/font-OFL%201.1-222222)

## Preview

![Bitcoin Austria beamer style — sample slides](example/preview.png)

A rendered sample of the current style. The full deck is committed at
**[`example/demo.pdf`](example/demo.pdf)** — open it for a quick look without
building anything. (Both the PDF and the montage above are regenerated from
`example/demo.tex`; rebuild with `cd example && make`.)

## What's in here

| Path | Purpose |
|------|---------|
| `bitcoin-austria.sty` | the Beamer style package |
| `fonts/` | Blinker typeface (SIL OFL 1.1) + license |
| `assets/` | logo (dark logomark + horizontal lockup), PNG for builds, SVG sources |
| `example/` | a minimal demo deck that doubles as the CI self-test |

**Brand:** light-grey `#ECECEC` canvas · red `#E3000F` accent · black `#222222`
text · Blinker font · dark logomark top-left · running title centre · frame
number top-right · bold headlines with a short red accent rule.

Slide macros provided by the package:

- `\comparisonslide{title}{Lhead}{Lbody}{Rhead}{Rbody}{noteHead}{noteBody}` —
  a two-column comparison (red accent left, dark accent right) with an optional
  full-width callout underneath.
- `\fillerslide[subtitle]{headline}` — a dark-background topic-divider slide
  (light logomark, white headline, red accent rule).
- `\fullbleedslide[caption]{image}` — a frame whose image fills the slide edge
  to edge, with an optional caption bar (e.g. a source URL).
- `\comparisontable{Lhead}{Rhead}{rows}` — a booktabs side-by-side comparison
  table (red left column, dark right column); used inside a frame.

Blocks are rectangular (sharp-edged) to match the brand's geometric style.

## Requirements

- **XeLaTeX** (the package loads Blinker via `fontspec`).
- A current LaTeX kernel (2020-10+) — uses `\CurrentFilePath` to self-locate.
- `latexmk` to build (recommended).

## Use it in a presentation (git submodule)

```bash
# from your presentation repo:
git submodule add git@github.com:<owner>/latex-beamer-style-2026.git theme
git commit -m "Add Bitcoin Austria beamer style as submodule"
```

In your `.tex` (compiled from the repo root), load it **by path**:

```latex
\documentclass[aspectratio=169,t,9pt]{beamer}
\usepackage{theme/bitcoin-austria}   % theme/ = the submodule directory
```

The package finds its own `fonts/` and `assets/` automatically, wherever the
submodule is mounted. If auto-detection ever fails, set the directory yourself
before loading:

```latex
\def\bitcoinaustriaroot{theme/}      % note the trailing slash
\usepackage{theme/bitcoin-austria}
```

> **Cloning a repo that uses this theme:** the submodule must be checked out, or
> the build fails with a missing-package error:
> ```bash
> git clone --recurse-submodules <repo-url>
> # or, in an existing clone:
> git submodule update --init --recursive
> ```

## Build the demo

```bash
cd example
latexmk -xelatex demo.tex      # -> demo.pdf
```

## Licensing

- Package code (`bitcoin-austria.sty`, build files): **Apache-2.0** (see `LICENSE`).
- **Blinker** font: **SIL Open Font License 1.1** (see `fonts/BLINKER-OFL-License.txt`).
- Bitcoin Austria logo/marks: © Bitcoin Austria — brand assets, used for
  Bitcoin Austria presentations.
