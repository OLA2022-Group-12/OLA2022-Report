SRCS=\
	$(wildcard appendices/*) \
	$(wildcard chapters/*) \
	$(wildcard csvtables/*) \
	$(wildcard img/*) \
	$(patsubst graphs/%.txt,graphs/%.latex,$(wildcard graphs/*.txt)) \
	$(wildcard listings/*) \
	$(wildcard papers/*) \
	report.bib \
	title.tex \
	report.tex

LATEX_FLAGS=-shell-escape
BIBER_FLAGS=

mkdir = @mkdir -p $(@D)

report.pdf: $(SRCS)
	$(mkdir)
	pdflatex $(LATEX_FLAGS) report
	biber $(BIBER_FLAGS) report
	pdflatex $(LATEX_FLAGS) report
	pdflatex $(LATEX_FLAGS) report

graphs/%.latex: graphs/%.txt
	$(mkdir)
	-plantuml -quiet -tlatex $<

clean:
	-rm \
		report-gnuplottex* \
		report.{gnuploterrors,aux,bbl,bcf,blg,lof,log,lol,lot,out,pdf,run.xml,toc,acn,acr,alg,glg,glo,gls,ist,tdo} \
		glossaries.aux
.PHONY: clean

