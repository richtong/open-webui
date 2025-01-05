SHELL := /usr/bin/env bash

PYTHON ?= 3.12.4

.DEFAULT_GOAL := help
.PHONY: help
# https://marmelab.com/blog/2016/02/29/auto-documented-makefile.html does not
# work because we use an include file
# https://swcarpentry.github.io/make-novice/08-self-doc/ is simpler just need
# and it dumpes them out relies on the variable MAKEFILE_LIST which is a list of
# all files note we do not just use $< because this is an include.mk file
## help: available commands (the default)
help: $(MAKEFILE_LIST)
	@sed -n 's/^##//p' $(MAKEFILE_LIST)

## install: create uv environment
.PHONY: install
install:
	brew install uv make
	uv venv -p $(PYTHON)
	uv pip install -r requirements.txt

## dev: start the development server
.PHONY: dev
dev:
	uv run dev.sh
