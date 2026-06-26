# Build the Bitcoin Austria style demo.
.PHONY: all clean watch

all: demo.pdf

demo.pdf: demo.tex ../bitcoin-austria.sty
	latexmk -xelatex -interaction=nonstopmode -halt-on-error demo.tex

watch:
	latexmk -xelatex -pvc -interaction=nonstopmode demo.tex

clean:
	latexmk -C
	rm -f *.nav *.snm *.vrb build.log
