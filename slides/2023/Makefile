OUT:=$(HOME)/Web/site/slides/2023/bsc
TGT_HTML:=$(patsubst %.md, $(OUT)/%.html, index.md $(wildcard 0*.md))
TGT_IMG:=$(patsubst images/%, $(OUT)/images/%, $(wildcard images/*))
TGT_IMG:=$(TGT_IMG:.gv=.svg)

all: $(TGT_HTML) $(TGT_IMG)

%: $(OUT)/%.html
	@date '+%Y-%m-%d %H:%M:%S "$<" done'

$(OUT)/%.html: %.md defaults.yaml template.html
	pandoc --defaults=defaults.yaml $< -o $@

images/%.svg: gv/%.gv
	dot -Tsvg -o $@ $^

$(OUT)/images/%: images/%
	cp $^ $@
	chmod a+r $@
