plantuml ?= $(shell command -v plantuml)
ifeq ($(strip $(plantuml)),)
$(error required plantuml not found. To install plantuml see https://plantuml.com/starting)
endif

%.png: %.puml ; cat $< | plantuml -pipe > $@

PUML_FILES := $(wildcard *.puml)

PNG_FILES := $(PUML_FILES:.puml=.png)

pngs: $(PNG_FILES)

clean: ; $(RM) $(PNG_FILES)
