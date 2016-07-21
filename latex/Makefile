

NAME = vtkDiscreteMarchingCubes_extension

BIBTEXDATABSENAME = ${NAME}


all: pdf


pdf: ${NAME}.pdf



${NAME}.pdf: ${NAME}.tex  ${BIBTEXDATABSENAME}.bib
	pdflatex -shell-escape ${NAME}.tex
	bibtex ${NAME}
	pdflatex ${NAME}.tex
	pdflatex ${NAME}.tex


${NAME}.bbl: ${BIBTEXDATABSENAME}.bib ${NAME}.aux
	bibtex ${NAME}


tot.bib : ~/jabref/diss.bib ~/jabref/software.bib
	cat ~/jabref/diss.bib ~/jabref/software.bib | sed '/[Ff]ile[[:space:]]*=/d;/[Oo]wner[[:space:]]*=/d' | ~/bin/preserve_capitalization.pl >| tot.bib


${BIBTEXDATABSENAME}.bib : ${BIBTEXDATABSENAME}.aux tot.bib
	java -jar ~/programme/jabref/jabref.jar -n -a $<,$@ tot.bib
	-rm -v ${BIBTEXDATABSENAME}.bib.bak


${NAME}.aux: ${NAME}.tex  ${BIBTEXDATABSENAME}.bib
	pdflatex ${NAME}.tex



clean:
	-rm ${NAME}.dvi ${NAME}.ps ${NAME}.pdf ${NAME}.aux ${NAME}.log ${NAME}.bbl ${NAME}.blg ${NAME}.toc ${NAME}.out  ${NAME}.brf
	-rm tot.bib


vtkDiscreteMarchingCubes_extension_01+02.jpg : images/vtkDiscreteMarchingCubes_extension_01.png  images/vtkDiscreteMarchingCubes_extension_02.png
	montage $^ -geometry 1024x+0+0 -tile 1x2 -quality 93  $@
