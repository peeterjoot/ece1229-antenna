FIGPATH := ../../figures/ece1229-antenna/project
PNGPATHS := $(wildcard $(FIGPATH)/*.png)
JPGPATHS := $(wildcard $(FIGPATH)/*.jpg)
#PNGFIGURES := $(notdir $(PNGPATHS))
#JPGFIGURES := $(notdir $(JPGPATHS))
PDFLATEX := pdflatex -file-line-error -synctex=1 --max-print-line=1000 --c-style-errors --halt-on-error
#DIST := /cygdrive/c/Users/IBM_ADMIN/Dropbox/ece1229-handouts/project/report

TOP := $(shell pwd)

all : presentation.pdf
#all : pr.pdf

#presentation.pdf : $(FIGURES)
presentation.pdf : Bibliography.bib xingqi.tex peeter.tex figpath.sty

#$(PNGFIGURES) : %.png: $(FIGPATH)/%.png
#	cp $< $@
#
#$(JPGFIGURES) : %.jpg: $(FIGPATH)/%.jpg
#	cp $< $@

%.pdf :: %.tex
	$(PDFLATEX) $<
	bibtex $(basename $@)
	$(PDFLATEX) $<
	bibtex $(basename $@)
	$(PDFLATEX) $<
	bibtex $(basename $@)

#dist : 
#	cp make.sh $(PNGPATHS) $(JPGPATHS) *.pdf Bibliography.bib peeter.tex  presentation.tex  xingqi.tex $(DIST)
#	cp figpathdist.sty $(DIST)/figpath.sty

clean :
	rm -f *.snm *.aux *.out *.toc *.nav *.pdf *.synctex.gz *.log *.blg *.bbl *.png *.pdf *.bib

Bibliography.bib : ../Bibliography.bib
	cp $^ $@

#Bibliography.bib : ../../latex/myrefs.bib.in
#	cp ../../latex/myrefs.bib.in myrefs.bib
#	(cd ../.. ; ./METADATA -bib >> $(TOP)/myrefs.bib)
#	sed 's/@webpage/@manual/g' < myrefs.bib > Bibliography.bib
