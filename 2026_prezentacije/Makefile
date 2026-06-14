SHELL := /bin/sh

.DEFAULT_GOAL := all
.PHONY: all new build clean-aux

TEMPLATE_DIR := template
TEMPLATE_FILES := \
	beamercolorthemewildcat.sty \
	beamerfontthemewildcat.sty \
	beamerinnerthemewildcat.sty \
	beamerouterthemewildcat.sty \
	beamerthemewildcat.sty

LATEX := xelatex -interaction=nonstopmode -halt-on-error
AUX_PATTERNS := *.aux *.bbl *.bcf *.blg *.dvi *.fdb_latexmk *.fls *.ilg *.ind *.idx *.lof *.log *.lot *.nav *.out *.run.xml *.snm *.synctex.gz *.toc *.thm *.vrb *.xdv

################################################################################
# new: create a presentation folder with minimal files
################################################################################
new:
	# require name at runtime (avoid parse-time conditionals)
	if [ -z "$(name)" ]; then echo "You must provide a name. Usage: make new name=your_folder_name" >&2; exit 1; fi; \
	set -e; \
	if [ -e "$(name)" ] && [ ! -d "$(name)" ]; then echo "$(name) exists and is not a directory" >&2; exit 1; fi; \
	mkdir -p "$(name)"; \
	for file in $(TEMPLATE_FILES); do \
		if [ -f "$(TEMPLATE_DIR)/$$file" ] && [ ! -f "$(name)/$$file" ]; then cp "$(TEMPLATE_DIR)/$$file" "$(name)/"; fi; \
	done; \
	if [ ! -f "$(name)/$(name).tex" ]; then \
		printf '%s\n' \
			'\documentclass[aspectratio=1610]{beamer}' \
			'' \
			'\title{$(name)}' \
			'\author{Your Name}' \
			'\date{\today}' \
			'' \
			'\usetheme[sectionpage=none]{wildcat}' \
			'' \
			'\begin{document}' \
			'' \
			'\begin{frame}' \
			'\titlepage' \
			'\end{frame}' \
			'' \
			'\begin{frame}{Outline}' \
			'\tableofcontents' \
			'\end{frame}' \
			'' \
			'\section{Introduction}' \
			'' \
			'\begin{frame}{Introduction}' \
			'    Your content starts here.' \
			'\end{frame}' \
			'' \
			'\end{document}' > "$(name)/$(name).tex"; \
	fi; \
	echo "Created/updated folder '$(name)'"

################################################################################
# build: build a single presentation (fails if folder or tex missing)
################################################################################
build:
	# require name at runtime (avoid parse-time conditionals)
	if [ -z "$(name)" ]; then echo "You must provide a name. Usage: make build name=your_folder_name" >&2; exit 1; fi; \
	set -e; \
	if [ ! -d "$(name)" ]; then echo "Directory '$(name)' does not exist. Run 'make new name=$(name)' to create it." >&2; exit 2; fi; \
	if [ ! -f "$(name)/$(name).tex" ]; then echo "No TeX file '$(name)/$(name).tex' found in $(name). Run 'make new name=$(name)' to create a starter file." >&2; exit 3; fi; \
	echo "Building $(name)/$(name).tex..."; \
	( cd "$(name)" && $(LATEX) "$(name).tex" && $(LATEX) "$(name).tex" ); \
	$(MAKE) --no-print-directory clean-aux name="$(name)"; \
	echo "Built '$(name)/$(name).pdf'"

################################################################################
# all: build all existing folders that contain a matching tex file (skip others)
################################################################################
all:
	@set -e; \
	for dir in $$(find . -maxdepth 1 -mindepth 1 -type d ! -name template -printf '%f\n' | sort); do \
		if [ -f "$$dir/$$dir.tex" ]; then \
			$(MAKE) --no-print-directory build name="$$dir"; \
		else \
			echo "Skipping '$$dir' (no $$dir.tex)"; \
		fi; \
	done

################################################################################
# clean-aux: remove auxiliary files for a specific folder
################################################################################
clean-aux:
	# require name at runtime (avoid parse-time conditionals)
	if [ -z "$(name)" ]; then echo "You must provide a name. Usage: make clean-aux name=your_folder_name" >&2; exit 1; fi; \
	# remove only known LaTeX auxiliary/output files listed in AUX_PATTERNS
	# keep all source files (*.tex, *.sty, images, etc.) and PDFs
	set -e; \
	for pat in $(AUX_PATTERNS); do \
		find "$(name)" -maxdepth 1 -type f -name "$$pat" -print0 | xargs -0 --no-run-if-empty rm -f --; \
	done; \
	echo "Cleaned auxiliary files in '$(name)' (kept sources and PDFs)"
