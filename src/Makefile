# Makefile for Sphinx documentation

# You can set these variables from the command line.
SPHINXOPTS    =
SPHINXBUILD   = poetry run sphinx-build
BUILDDIR      = build
WEBAPPDIR     = ../doc/prod

# Internal variables.
ALLSPHINXOPTS = -d $(BUILDDIR)/doctrees $(SPHINXOPTS) source

.PHONY: help clean install html

help:
	@echo "Please use \`make <target>' where <target> is one of"
	@echo "  install       to build HTML files and install them under $(abspath $(WEBAPPDIR))"
	@echo "  clean         to clean the build directory"

install: html
	@echo "Installing documentation..."
	@rm -rf $(WEBAPPDIR)
	@mv $(BUILDDIR)/html $(WEBAPPDIR)
	@echo "Install finished. The HTML pages are in $(WEBAPPDIR)."

html: check-poetry
	@echo "Building HTML documentation..."
	$(SPHINXBUILD) -b html $(ALLSPHINXOPTS) $(BUILDDIR)/html
	@echo "Build finished. The HTML pages are in $(BUILDDIR)/html."

clean:
	@echo "Cleaning build directory..."
	@rm -rf $(BUILDDIR)/*

.PHONY: check-poetry
check-poetry:
	@if ! command -v poetry &> /dev/null; then \
		echo 'Error: poetry is not installed. Please install poetry.'; \
		exit 1; \
	fi
	@poetry install
