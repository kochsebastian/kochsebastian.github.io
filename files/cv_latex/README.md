# cv_latex

LaTeX port of the MS Word CV template (`cv_2026_3page.docx`), visually matched
to the reference PDF (`cv_2026_3page.pdf`) — same 3-page layout, page breaks,
fonts, and spacing (every text line within ~2pt of the original at 150 dpi).

## Build

```sh
make            # or: latexmk -xelatex cv.tex
```

Requires **XeLaTeX** (TeX Live) and these fonts:

| Use                    | Font              | Source                          |
| ---------------------- | ----------------- | ------------------------------- |
| Body                   | Roboto            | system / TeX Live               |
| Name (fake small caps) | Arial             | system (macOS/Windows/Overleaf) |
| Header serif line      | Times New Roman   | system                          |
| Header URL             | Carlito           | TeX Live (`carlito` package)    |
| Header icons           | FontAwesome 5     | TeX Live (`fontawesome5`)       |

Works on Overleaf: set the compiler to XeLaTeX.

## Structure (`cv.tex`)

- `\cvsection[<space above>]{<title>}` — bold section title with 1pt rule.
- `cvtable` environment — `longtable` with a right-aligned gray date column,
  1pt gray divider, and a content column; breaks across pages like Word
  tables. The date column width is given per section (Word cell widths):
  `0.831in` education/experience, `0.421in` honors, `0.441in` publications
  and talks.
- `\company{...}` — full-width bold employer row (no divider).
- `\bitem` / `\bitemj` / `\bitems` — bullets (left-aligned / justified /
  small 9.5pt), hanging bullet like Word's list indent.
- `\pubitem{...}` — publication with 0.221in hanging indent.

Spacing constants (line grids, gaps) were measured from the reference PDF and
are documented next to their definitions; the geometry derives from the Word
table layout rather than absolute positioning, so content edits reflow
naturally.

Deliberate deviations from the Word file: FontAwesome icons instead of
embedded PNGs, a real `\LaTeX` logo instead of the image, and real hanging
indents instead of Word's space-padding hacks. All hyperlinks from the
original are preserved.
