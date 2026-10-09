OUT:=../../site/2026
SHARED:=../shared/images
SITE_SHARED:=$(OUT)/../shared/images
TGT_HTML:=$(patsubst %.md, $(OUT)/%.html, $(wildcard *.md))
TGT_IMG:=$(patsubst $(SHARED)/%, $(SITE_SHARED)/%, $(wildcard $(SHARED)/*g) $(wildcard $(SHARED)/*.webp)) $(patsubst images/%, $(OUT)/images/%, $(wildcard images/*ng) $(wildcard images/*pg) $(wildcard images/*/*g) $(wildcard images/*/*/*g))
TGT_IMG:=$(TGT_IMG:.gv=.svg)

all: $(TGT_HTML) $(TGT_IMG)

%: $(OUT)/%.html
	@date '+%Y-%m-%d %H:%M:%S "$(notdir $<)" done'

$(OUT)/%.html: %.md defaults.yaml template.html
	@mkdir -p $(OUT)
	pandoc --defaults=defaults.yaml $< -o $@

images/%.svg: gv/%.gv
	dot -Tsvg -o $@ $^

$(SITE_SHARED)/%: $(SHARED)/%
	@mkdir -p $(dir $@)
	@ln -f '$^' '$@'
	@chmod a+r '$@'
	@echo '$@'

$(OUT)/images/%: images/%
	@mkdir -p $(dir $@)
	@ln -f '$^' '$@'
	@chmod a+r '$@'
	@echo $@

serve: all
	cd ../../site ; python3 -m http.server 8001


## Use https://unsplash.com/ and https://www.pexels.com/ for free images.

