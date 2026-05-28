SHELL := /bin/bash
PDFLATEX := pdflatex -interaction=nonstopmode -halt-on-error

BASE := .
AUX_PATTERNS := *.aux *.bbl *.bcf *.blg *.dvi *.fdb_latexmk *.fls *.ilg *.ind *.idx *.lof *.log *.lot *.nav *.out *.run.xml *.snm *.synctex.gz *.toc *.thm *.vrb *.xdv

.PHONY: all main clean clean-aux-main

all: main

main:
	cd $(BASE) && $(PDFLATEX) main.tex && $(PDFLATEX) main.tex
	mv -f $(BASE)/main.pdf $(BASE)/kriptografija_napredne_teme.pdf
	$(MAKE) clean-aux-main

clean-aux-main:
	@rm -f $(BASE)/$(AUX_PATTERNS)

clean:
	$(MAKE) clean-aux-main
	@rm -f $(BASE)/*.pdf
