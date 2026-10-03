OUT:=$(HOME)/Web/site/slides/2022/talks
# OUT:=.
SHARED:=../shared/images
SITE_SHARED:=$(OUT)/../shared/images
TGT_HTML:=$(patsubst %.md, $(OUT)/%.html, $(wildcard *.md))
TGT_IMG:=$(patsubst $(SHARED)/%, $(SITE_SHARED)/%, $(wildcard $(SHARED)/*g)) $(patsubst images/%, $(OUT)/images/%, $(wildcard images/*))

all: $(TGT_HTML) $(TGT_IMG)

$(OUT)/%.html: %.md defaults.yaml template.html
	pandoc --defaults=defaults.yaml $< -o $@
	@date '+%Y-%m-%d %H:%M:%S "$<" done'

$(SITE_SHARED)/%: $(SHARED)/%
	@mkdir -p $(dir $@)
	cp $^ $@

$(OUT)/images/%: images/%
	cp $^ $@
