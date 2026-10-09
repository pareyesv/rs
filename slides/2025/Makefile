OUT:=../../site/2025
SHARED:=../shared/images
SITE_SHARED:=$(OUT)/../shared/images
TGT_HTML:=$(patsubst %.md, $(OUT)/%.html, $(wildcard *.md))
TGT_IMG:=$(patsubst $(SHARED)/%, $(SITE_SHARED)/%, $(wildcard $(SHARED)/*g)) $(patsubst images/%, $(OUT)/images/%, $(wildcard images/*.png) $(wildcard images/*.jpg) $(wildcard images/*.jpeg) $(wildcard images/*.gif) $(wildcard images/*.svg) $(wildcard images/*.webp) $(wildcard images/*/*g) $(wildcard images/*/*/*g))

all: $(TGT_HTML) $(TGT_IMG)

%: $(OUT)/%.html
	@date '+%Y-%m-%d %H:%M:%S "$(notdir $<)" done'

$(OUT)/%.html: %.md defaults.yaml template.html
	@mkdir -p $(OUT)
	pandoc --defaults=defaults.yaml $< -o $@

$(SITE_SHARED)/%: $(SHARED)/%
	@mkdir -p $(dir $@)
	@ln -f '$^' '$@'
	@chmod a+r '$@'
	@echo '$@'

$(OUT)/images/%: images/%
	@mkdir -p $(dir $@)
	@ln -f '$^' '$@'
	@chmod a+r '$@'
	@echo '$@'

serve: all
	cd ../../site ; python3 -m http.server
