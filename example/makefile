# Build the Bitcoin Austria style demo in both aspect ratios.
#   demo.pdf      16:9  (the standard)
#   demo-43.pdf   4:3
# Both decks share their slides via demo-common.tex.
.PHONY: all preview clean watch

all: demo.pdf demo-43.pdf

demo.pdf: demo.tex demo-common.tex ../bitcoin-austria.sty
	latexmk -xelatex -interaction=nonstopmode -halt-on-error demo.tex

demo-43.pdf: demo-43.tex demo-common.tex ../bitcoin-austria.sty
	latexmk -xelatex -interaction=nonstopmode -halt-on-error demo-43.tex

# Regenerate the committed README previews (needs poppler + ImageMagick).
# A 3x3 montage of each deck's nine slides. Run locally after changing the demo;
# CI only builds the PDFs (it has no ImageMagick).
preview: preview.png preview-43.png

preview.png: demo.pdf
	pdftoppm -png -r 110 demo.pdf $@-page
	montage $@-page-*.png -tile 3x3 -geometry +6+6 -background '#cfcfcf' $@
	rm -f $@-page-*.png

preview-43.png: demo-43.pdf
	pdftoppm -png -r 110 demo-43.pdf $@-page
	montage $@-page-*.png -tile 3x3 -geometry +6+6 -background '#cfcfcf' $@
	rm -f $@-page-*.png

watch:
	latexmk -xelatex -pvc -interaction=nonstopmode demo.tex

clean:
	latexmk -C demo.tex demo-43.tex
	rm -f *.nav *.snm *.vrb build.log *-page-*.png
