aasvg ?= $(shell command -v aasvg)
ifeq ($(strip $(aasvg)),)
$(error required aasvg not found.  To install it: npm install -g aasvg)
endif

%.svg: %.ascii ; cat $< | aasvg --backdrop > $@

ASCII_FILES := $(wildcard *.ascii)

SVG_FILES := $(ASCII_FILES:.ascii=.svg)

svgs: $(SVG_FILES)

clean: ; $(RM) $(SVG_FILES)
