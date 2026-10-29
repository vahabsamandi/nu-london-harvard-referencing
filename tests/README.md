# Smoke test

Run from within tests/ with a TeX Live installation that includes BibLaTeX and Biber:

~~~sh
TEXINPUTS=..: pdflatex -interaction=nonstopmode -halt-on-error main.tex
biber main
TEXINPUTS=..: pdflatex -interaction=nonstopmode -halt-on-error main.tex
TEXINPUTS=..: pdflatex -interaction=nonstopmode -halt-on-error main.tex
~~~

Check the PDF for the organisation name, italic *et al.*, and the ProQuest retrieval wording.
