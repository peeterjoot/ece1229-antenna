THISDIR := ece1229-antenna
THISBOOK := ece1229

BIBLIOGRAPHY_PATH := classicthesis_mine
HAVE_OWN_CONTENTS := 1
HAVE_OWN_TITLEPAGE := 1
MY_CLASSICTHESIS_FRONTBACK_FILES += ../latex/classicthesis_mine/FrontBackmatter/Index.tex
MY_CLASSICTHESIS_FRONTBACK_FILES += ../latex/classicthesis_mine/FrontBackmatter/ContentsAndFigures.tex
BOOKTEMPLATE := ../latex/classicthesis_mine/ClassicThesis2.tex

include make.revision
include ../latex/make.bookvars

# comment this out for online pdf version (uncomment for KDP)
#PRINT_VERSION := 1
#ifdef KINDLE_VERSION
#PARAMS += --kindle
#endif
#ifdef PRINT_VERSION
#SUBFIGDIR := bw
#else
#SUBFIGDIR := color
#endif
ifndef PRINT_VERSION
PARAMS += --no-print
endif
#PARAMS += -subfig $(SUBFIGDIR)
#DISTEXTRA := $(SUBFIGDIR)
ifdef PRINT_VERSION
DISTEXTRA := kdp
#DISTEXTRA := $(DISTEXTRA).kdp
endif



#ONCEFLAGS := -justonce

SOURCE_DIRS += appendix
FIGURES := ../figures/$(THISDIR)
SOURCE_DIRS += $(FIGURES)

PRIMARY_SOURCES += FrontBackmatter/preface.tex

GENERATED_SOURCES += matlab.tex 
GENERATED_SOURCES += mathematica.tex 
GENERATED_SOURCES += julia.tex 
GENERATED_SOURCES += backmatter.tex
 
EPS_FILES := $(wildcard $(FIGURES)/*.eps)
PDFS_FROM_EPS := $(subst eps,pdf,$(EPS_FILES))

THISBOOK_DEPS += $(PDFS_FROM_EPS)
THISBOOK_DEPS += macros_mathematica.sty
DO_SPELL_CHECK := $(shell cat spellcheckem.txt)

include ../latex/make.rules

.PHONY: spellcheck
spellcheck: $(patsubst %.tex,%.sp,$(filter-out $(DONT_SPELL_CHECK),$(DO_SPELL_CHECK)))

%.sp : %.tex
	spellcheck $^
	touch $@

$(THISBOOK).pdf :: $(EXTERNAL_DEPENDENCIES)

problemSets : advancedantennaProblemSet1.pdf advancedantennaProblemSet2.pdf advancedantennaProblemSet3.pdf advancedantennaProblemSet4.pdf advancedantennaProblemSet5.pdf

advancedantennaProblemSet1.pdf : advancedantennaProblemSet1Problem1.tex
advancedantennaProblemSet1.pdf : advancedantennaProblemSet1Problem2.tex
advancedantennaProblemSet1.pdf : advancedantennaProblemSet1Problem3.tex
advancedantennaProblemSet1.pdf : advancedantennaProblemSet1Problem4.tex
advancedantennaProblemSet1.pdf : advancedantennaProblemSet1Problem5.tex
advancedantennaProblemSet1.pdf : advancedantennaProblemSet1Problem6.tex

advancedantennaProblemSet2.pdf : advancedantennaProblemSet2Problem1.tex
advancedantennaProblemSet2.pdf : advancedantennaProblemSet2Problem2.tex
advancedantennaProblemSet2.pdf : advancedantennaProblemSet2Problem3.tex
advancedantennaProblemSet2.pdf : advancedantennaProblemSet2Problem4.tex
advancedantennaProblemSet2.pdf : advancedantennaProblemSet2Problem5.tex

advancedantennaProblemSet3.pdf : advancedantennaProblemSet3Problem1.tex
advancedantennaProblemSet3.pdf : advancedantennaProblemSet3Problem2.tex
advancedantennaProblemSet3.pdf : advancedantennaProblemSet3Problem3.tex
advancedantennaProblemSet3.pdf : ps3mathematica.tex

advancedantennaProblemSet4.pdf : advancedantennaProblemSet4Problem1.tex
advancedantennaProblemSet4.pdf : advancedantennaProblemSet4Problem2.tex
advancedantennaProblemSet4.pdf : advancedantennaProblemSet4Problem3.tex
advancedantennaProblemSet4.pdf : advancedantennaProblemSet4Problem4.tex
advancedantennaProblemSet4.pdf : ps4mathematica.tex
advancedantennaProblemSet4.pdf : ps4matlab.tex
advancedantennaProblemSet4.pdf : ps4julia.tex

advancedantennaProblemSet5.pdf : advancedantennaProblemSet5Problem1.tex
advancedantennaProblemSet5.pdf : advancedantennaProblemSet5Problem2.tex
advancedantennaProblemSet5.pdf : ps5matlab.tex
advancedantennaProblemSet5.pdf : ps5mathematica.tex
advancedantennaProblemSet5.pdf : matlab.sty

ps5matlab.tex : ../METADATA ../matlab/METADATA
	(cd .. ; ./METADATA -matlab -latex -ece1229 -filter ece1229/ps5/ ) > $@

ps5mathematica.tex : ../METADATA ../mathematica/METADATA
	(cd .. ; ./METADATA -mathematica -latex -ece1229 -filter ece1229/ps5/ ) > $@

ps4mathematica.tex : ../METADATA ../mathematica/METADATA
	(cd .. ; ./METADATA -mathematica -latex -ece1229 -filter ece1229/ps4/ ) > $@

ps4matlab.tex : ../METADATA ../matlab/METADATA
	(cd .. ; ./METADATA -matlab -latex -ece1229 -filter ece1229/ps4/ ) > $@

ps4julia.tex : ../METADATA ../julia/METADATA
	(cd .. ; ./METADATA -julia -latex -ece1229 -filter ece1229/ps4/ ) > $@

ps3mathematica.tex : ../METADATA ../mathematica/METADATA
	(cd .. ; ./METADATA -mathematica -latex -ece1229 -filter ece1229/ps3/ ) > $@

# hack:
clean ::
	git checkout FrontBackmatter/Titlepage.tex

backmatter.tex: ../latex/classicthesis_mine/backmatter2.tex
	rm -f $@
	ln -s ../latex/classicthesis_mine/backmatter2.tex backmatter.tex
