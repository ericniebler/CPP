DOCNO = 1194
PD = D
SOURCE = p1194_executor_compromise_the_return.md
TARGET = $(PD)$(DOCNO)

PANDOC = pandoc
PANDOC_FORMAT = markdown_github+yaml_metadata_block+smart

$(TARGET).html: $(SOURCE) header.html pandoc-template.html pandoc.css
	$(PANDOC) -f $(PANDOC_FORMAT) -t markdown+smart -o $@.org -s $<
	$(PANDOC) -f markdown+smart -t html -o $@ --number-sections --toc -s --template=pandoc-template --include-before-body=header.html  --include-in-header=pandoc.css $<

$(TARGET).pdf: $(SOURCE)
	$(PANDOC) -f $(PANDOC_FORMAT) -t latex -o $@ --number-sections --toc -s $<

header.html: header.html.in Makefile
	sed 's/%%DOCNO%%/$(TARGET)/g' < $< > $@

clean:
	rm -f $(TARGET).html $(TARGET).pdf header.html *~

view: $(TARGET).html
	gnome-www-browser $(TARGET).html
