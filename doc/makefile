#############
# Settings
#############

#############
# Make options
#############

# Set the shell to be bash
SHELL:=/bin/bash

# Sane exit / error reporting options for bash
# errexit: exit bash with $? if $? != 0
# pipefail: a | b will exit with the first $? != 0 instead of the $? of b
export SHELLOPTS:=errexit:pipefail

# Delete target files on error
.DELETE_ON_ERROR:

# Disable built in suffix rules
.SUFFIXES:

# Disable builtin pattern rules
MAKEFLAGS+=-r

# Enable second expansion
.SECONDEXPANSION:

# Set default target
.DEFAULT_GOAL:=build

#############
# Variables
#############

# Pandoc compiler to use
PANDOC:=pandoc

# Extension for pandoc files
PANDOCEXT:=pdc

# Number headers
PANDOCOPTS+= -N

# Documents should be a standalone file
PANDOCOPTS+= -s

# Template to use
TEMPLATE:=gameinstructions.tex

# All the documents to build
DOCS:=$(patsubst %.$(PANDOCEXT),%.pdf,$(wildcard *.$(PANDOCEXT)))

# Verborsity settings. One to print commands, anything else to keep te build silent.
ifeq ($(V),1)
  Q:=
else
  Q:=@
endif

#############
# Rules
#############

# Build pandoc flavoured markdown reports to pdf
%.pdf: %.pdc $$(wildcard %_sections/*.pdc)
	$Q$(PANDOC) $(PANDOCOPTS) --template $(TEMPLATE) $^ -o $@

# Default rule - build everything
build: $(DOCS)

# Clean target
.PHONY:clean
clean:
	$Q$(RM) $(DOCS)
