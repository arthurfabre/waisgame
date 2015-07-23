PANDOC:=pandoc

PANDOCOPTS:=$(PANDOCOPTS)

# Number headers
PANDOCOPTS+= -N

# Report should be a standalone file
PANDOCOPTS+= -s

# All files
ALLREPORTS:=$(patsubst %.pdc,%.pdf,$(wildcard *.pdc))

# Default rule - build everything
all: $(ALLREPORTS)

# Build pandoc flavoured markdown reports to pdf
%.pdf: %.pdc
	@$(PANDOC) $(PANDOCOPTS) $< -o $@
