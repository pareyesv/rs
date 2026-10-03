OUT:=$(HOME)/Web/site/slides/2023/bsc
SHARED:=../shared/images
SITE_SHARED:=$(OUT)/../shared/images
TGT_HTML:=$(patsubst %.md, $(OUT)/%.html, index.md $(wildcard 0*.md))
TGT_IMG:=$(patsubst $(SHARED)/%, $(SITE_SHARED)/%, $(wildcard $(SHARED)/*g)) $(patsubst images/%, $(OUT)/images/%, $(wildcard images/*))

all: $(TGT_HTML) $(TGT_IMG)

%: $(OUT)/%.html
	@date '+%Y-%m-%d %H:%M:%S "$<" done'

$(OUT)/%.html: %.md defaults.yaml template.html
	pandoc --defaults=defaults.yaml $< -o $@

$(SITE_SHARED)/%: $(SHARED)/%
	@mkdir -p $(dir $@)
	cp $^ $@
	chmod a+r $@

$(OUT)/images/%: images/%
	cp $^ $@
	chmod a+r $@
