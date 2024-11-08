# Makefile for Sphinx documentation
#

# You can set these variables from the command line.
SPHINXOPTS    =
SPHINXBUILD   = poetry run sphinx-build
PAPER         =
BUILDDIR      = build
WEBAPPDIR     = ../doc/next

# Internal variables.
PAPEROPT_a4     = -D latex_paper_size=a4
PAPEROPT_letter = -D latex_paper_size=letter
ALLSPHINXOPTS   = -d $(BUILDDIR)/doctrees $(PAPEROPT_$(PAPER)) $(SPHINXOPTS) source

# needed for versioning, assumes a versioning line in conf.py like this:
# release = '0.115'
v:=$(shell grep 'release =' ./source/conf.py | sed 's/[^=]*=//' | sed -e 's/[\# "'\'']//g')

# the i18n builder cannot share the environment and doctrees with the others
I18NSPHINXOPTS  = $(PAPEROPT_$(PAPER)) $(SPHINXOPTS) source

.PHONY: help clean install html version

help:
	@echo "Please use \`make <target>' where <target> is one of"
	@echo "  install       to make standalone HTML files and install them under $(abspath $(WEBAPPDIR))"
	@echo "  install-version       to make standalone HTML files and install them under $(abspath ../doc/$(v)), using the version from conf.py ($(v))"

install-version: install version

version: check-version
	@echo "Will set version to $(v)"
	mkdir -p ../doc/$(v)
	cp -r $(WEBAPPDIR)/ ../doc/$(v)/
	rm -rf $(WEBAPPDIR)
	rm -rf ../doc/prod
	ln -s $(v) ../doc/prod
	@echo
	@echo "Versioning finished. New version is $(v)"

check-version:
	@if [ -z "$(v)" ]; then \
		echo "Error: release versioning parameter not set in conf.py"; \
		exit 1; \
	fi

.PHONY: check-poetry
check-poetry:
	@if ! command -v poetry &> /dev/null; then \
		echo 'Error: poetry is not installed. Please run "brew install poetry"'; \
		exit 1; \
	fi

.PHONY: poetry-install
poetry-install: check-poetry
	poetry install	

clean:
	-rm -rf $(BUILDDIR)/*

install: html
	-rm -rf $(WEBAPPDIR)
	-mv $(BUILDDIR)/html $(WEBAPPDIR)
	@echo
	@echo "Install finished. The HTML pages are in $(WEBAPPDIR)."

html: poetry-install
	$(SPHINXBUILD) -b html $(ALLSPHINXOPTS) $(BUILDDIR)/html
	@echo
	@echo "Build finished. The HTML pages are in $(BUILDDIR)/html."
