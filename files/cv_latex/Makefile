all: cv.pdf

cv.pdf: cv.tex
	latexmk -xelatex -interaction=nonstopmode cv.tex

clean:
	latexmk -c

distclean:
	latexmk -C

.PHONY: all clean distclean
