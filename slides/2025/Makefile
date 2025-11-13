OUT:=../../site/2025
TGT_HTML:=$(patsubst %.md, $(OUT)/%.html, $(wildcard *.md))
TGT_IMG:=$(patsubst images/%, $(OUT)/images/%, $(wildcard images/*))
TGT_IMG:=$(TGT_IMG:.gv=.svg)

all: $(TGT_HTML) $(TGT_IMG)

%: $(OUT)/%.html
	@date '+%Y-%m-%d %H:%M:%S "$(notdir $<)" done'

$(OUT)/%.html: %.md defaults.yaml template.html
	@mkdir -p $(OUT)
	pandoc --defaults=defaults.yaml $< -o $@

images/%.svg: gv/%.gv
	dot -Tsvg -o $@ $^

$(OUT)/images/%g: images/%g
	@mkdir -p $(OUT)/images
	@ln -f '$^' '$@'
	@chmod a+r '$@'
	@echo $@

serve: all
	cd ../../site ; python3 -m http.server
