OUT:=$(HOME)/Web/site/slides/2022/talks
# OUT:=.
IMG:=images
TGT_HTML:=$(patsubst %.md, $(OUT)/%.html, $(wildcard *.md))
TGT_IMG:=$(patsubst $(IMG)/%, $(OUT)/$(IMG)/%, $(wildcard $(IMG)/*))
TGT_IMG:=$(TGT_IMG:.gv=.svg)

all: $(TGT_HTML) $(TGT_IMG)

$(OUT)/%.html: %.md defaults.yaml template.html
	pandoc --defaults=defaults.yaml $< -o $@
	@date '+%Y-%m-%d %H:%M:%S "$<" done'

$(OUT)/$(IMG)/%.png: $(IMG)/%.png
	cp $^ $@

$(OUT)/$(IMG)/%.svg: $(IMG)/%.gv
	dot -Tsvg -o $@ $^
	@date '+%Y-%m-%d %H:%M:%S "$<" done'