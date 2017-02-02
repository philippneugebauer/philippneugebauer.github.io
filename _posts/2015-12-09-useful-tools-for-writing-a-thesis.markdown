---
layout: post
title: Useful Tools for Writing a Thesis with LaTeX
date: 2016-01-30 19:21:27 +0800
categories: latex thesis tools
---

This post presents and highlights useful and probably important tools for writing a thesis with LaTeX.
The tools are categorized in the following to allow the simple finding of appropriate tools for your thesis.
In general, the posts explains only existing methods from other authors so that I also reference my sources.

## MISQ Style

First, I needed to adopt the style of [MISQ](http://www.misq.org/) for my thesis. Luckily, Ryan Schützler created a wonderful [template](http://www.schuetzler.net/blog/latex-icis-template/) for the easy adoption. This template requires the usage of `biber` instead of `bibtex` for the bibliography management. `biber` enables simple changes of citation styles and reuses the `bibtex` infrastructure so that only slight changes must be conducted. In detail, [[1]](https://de.sharelatex.com/learn/Biblatex_citation_styles) presents `biber` and the different citation styles. [[2]](https://verbosus.com/bibtex-style-examples.html?lang=en) provides a great overview on the different `bibtex` styles which I found very helpful when they were missing.

## Font Change

I never liked the default font style of LaTeX and even a particular font was prescribed for my thesis.
Unfortunately, font change handling can be quite complex since many side-effects must be considered.
Depending on the used font type, the math support may need to be reenabled.

    \usepackage{helvet}
    \usepackage[eulergreek]{sansmath}

When you are using the `tikz` package, you also need to change its default font [[3]](http://tex.stackexchange.com/questions/4887/pgf-tikz-and-sans-serif-fonts):

    \renewcommand{\familydefault}{\sfdefault}

Furthermore, the url font must be adapted [[4]](http://tex.stackexchange.com/questions/667/typeset-url-in-a-non-typewriter-font):

    \urlstyle{\sfdefault}

## Booktabs

Although many people consider the creation of tables simple, many mistakes can be done, even though the look of tables can be easily improved. The booktabs package for LaTeX is a good and simple way for improving the look, understanding and speed of information adoption. I found a great [guide](https://www.inf.ethz.ch/personal/markusp/teaching/guides/guide-tables.pdf) from [Markus Püschel](www.ece.cmu.edu/~pueschel) with further and detailled information. Restrictively, dashed separation lines were considered as appropriate, but they shouldn't be realized with the `arydshline` package. It introduces problems with the `booktabs` package [[5]](http://tex.stackexchange.com/a/267349/77450), seems to break their space alignment [[6]](http://tex.stackexchange.com/questions/257912/longtable-duplicate-separator-at-page-break#comment618493_257912) and even the loading of the package can lead to compilation errors [[8]](http://tex.stackexchange.com/questions/267304/remove-spacing-below-above-top-bottomrule/267308). On the downside, alternative colored rows for a better row separation are harder to implement with `booktabs`. Considering these instructions [[1]](http://tex.stackexchange.com/questions/267304/remove-spacing-below-above-top-bottomrule), my LaTeX table code is presented in the following:

{% gist 8242f90c61ab1acd6f97 %}

## General Table Look Improvements

This paragraph presents various possibilities to enhance the looking of LaTeX tables.
First, too long table captions are by default poorly rendered which can be resolved through the using of the `caption` package [[7]](http://tex.stackexchange.com/questions/16128/how-to-force-to-center-the-table-captions):

    \usepackage[justification=centering]{caption}

Secondly, very long `booktabs` tables can be improved with the alternative coloring of rows ([guide](https://www.inf.ethz.ch/personal/markusp/teaching/guides/guide-tables.pdf)), which is easily implemented through the `rowcolors` command and a color package [[4]](http://texblog.org/2011/09/02/coloring-every-alternate-table-row/).

    \rowcolors{<starting row index>}{<odd row color>}{<even row color>}

On the downside, the alternative row coloring only colors the rows, so that a workaround is required to color the space between the last row and the end line of the table. This is solved by [[8]](http://tex.stackexchange.com/questions/241851/table-row-color-covers-text/241866#241866) which changes the settings of the default `booktabs` table rules:

{% gist 662a0b0fca3df7e8a954 %}

Furthermore, `booktabs` requires another solution for the size adjustment of colored rows because it removes the trailing space of the rows at the beginning and end. This can be fixed through `kern` [[9]](http://tex.stackexchange.com/questions/177202/booktabs-and-row-color/177285#177285):

    \begin{tabular}{>{\kern-\tabcolsep}*{x}{>$c<$}<{\kern-\tabcolsep}}

Next, `multirows` requires the alignment of single lines through optional parameters [[10]](http://tex.stackexchange.com/questions/156219/proper-centering-with-cmidrule-and-multi-row-and-column/156222#156222):

    \multirow{2}[3]{*}{Sample}

Thereby, also `cmidrule` has an optional aligning parameter which you should use:

    \cmidrule(lr)

The `longtable` environment introduced the problem of bad caption spacing which can be resolved by using the `caption` package [[11]](http://tex.stackexchange.com/questions/20275/longtables-and-caption-spacing-problem/20286#20286).

    \usepackage{caption}
    \captionsetup[longtable]{skip=1em}

If you need a vertical `longtable` environment, employ the `pdflscape` package [[12]](http://tex.stackexchange.com/questions/242015/landscape-oriented-table-over-multiple-pages).

    \usepackage{pdflscape}
    ...
    \begin{landscape}
    \begin{longtable}
    ...
    \end{longtable}
    \end{landscape}

Lastly, the `cmidrule` needs an adaption if you have a very long table header, so that the content is centered below and looks good [[13]](http://tex.stackexchange.com/questions/267309/centering-of-content-below-cmidrule).

{% gist c0e7348485e8099dcfdc %}

## Tikz Diagrams

Using `tikz` is a great oppurtunity to include good-looking diagrams into your LaTeX document.
Saying that, a few settings can improve the look even more.
The alignment of associated values can be enhanced by appending them [[14]](http://tex.stackexchange.com/questions/51095/reduce-font-size-and-keep-label-position-in-bar-chart-using-pgf-tikz):
    every node near coord/.append style={font=\tiny}

Another simple upgrade is the avoidance of exponents in the axis labeling [[15]](http://www.mrunix.de/forums/showthread.php?72358-pgfplots-Achsenbeschriftung):

    scaled ticks=false,xticklabel style={/pgf/number format/fixed,/pgf/number format/precision=4}

Regarding these two fixes, my final design of bars was also influenced by these described designs and their code ([[16]](http://tex.stackexchange.com/questions/46316/how-to-put-the-values-of-each-bar-in-a-pgfplots-bar-chart-inside-the-bar-itself), [[17]](http://tex.stackexchange.com/questions/152143/grouped-bar-chart-with-pgfplots), [[18]](http://tex.stackexchange.com/questions/199142/how-to-draw-latex-multiple-bar-chart-with-error-bar)). The next listing presents my bar chart design.

{% gist 5a303fe46cb27e8363a1 %}

## PDF Compilation Speedup

After approaching the look enhancement, this paragraph lists the speed up opportunities for the compilation step.

Although the application of `tikz` provides nice features, a special adaption is required to improve its performance.
The externalization of such diagrams is a possibility and can be realized with the following settings according to its documentation [[19, Section 50.4]](http://ctan.unsw.edu.au/graphics/pgf/base/doc/pgfmanual.pdf).

    \usetikzlibrary{external}
    \tikzexternalize

Furthermore, the compilation process commands must be adapted:

    pdflatex -shell-escape

Since that's only a very simple example, a setup for big files with a lot of diagrams is preferable.
[[20]](http://tex.stackexchange.com/questions/1460/script-to-automate-externalizing-tikz-graphics/1475#1475) suggests it:

    \tikzexternalize[prefix=figures/]

    \tikzsetnextfilename{diagram1}
    \begin{tikzpicture}
    ...
    \end{tikzpicture}

Another chance is enabled by the right selection of the data type and its settings. [[21]](http://tex.stackexchange.com/questions/10966/quickest-way-to-include-graphics/10970#10970) presents and evaluates that:

    Photos: Use the JPG format and crop it to the size and viewport your need using an image processing program, e.g. Gimp or Photoshop. DO NOT use JPG for anything else, it is really just thought for photos. It can handle other stuff as well but not as good as other formats.

    Screenshoots and other Artificial Pixel-graphics: Use PNG format and again crop it to the size and viewport needed. The PNG format is lossless, i.e. doesn't create artifacts like JPG. Its compresses this kind of images well.

    Diagrams, Pictures and other Vector-graphics: Should really be included as vector-graphics and not as pixel-graphics (and if so NOT as JPG!). You should export them as PDF or EPS which is then converted to PDF
    (e.g. epstopdf). Extra whitespace from margins etc. can be removed by pdfcrop.

Beside that, the compilation command setup of LaTeX can be further improved [[22]](http://tex.stackexchange.com/questions/8791/speeding-up-latex-compilation). Since three compilation executions are in general recommended, the first two executions can be conducted without regarding pictures through `-draftmode`:

    pdflatex -draftmode file

The split-up of documents in subdocuments and their isolated compilation enables as well as the avoidance of the `input` command a further performance boost [[23]](http://www.howtotex.com/tips-tricks/faster-latex-part-i-compile-only-parts/). Also other compilation setups like `pdflatex -interaction=batchmode` are considered to enhance the compilation time [[24]](http://tex.stackexchange.com/questions/8791/speeding-up-latex-compilation). The `syntonly` package [[25]](http://www.howtotex.com/tips-tricks/faster-latex-part-iii-check-syntax-only/) and a precompiled preamble accelerate the speed as well [[26]](http://www.howtotex.com/tips-tricks/faster-latex-part-iv-use-a-precompiled-preamble/), but I haven't utilized them in my thesis. In general, use as few packages as possible and only include required packages because useless packages can slow down the compilation or cause problems! 

## Code Listing Formatting

Since I was studying computer science, code was an essential part of my thesis.
You can take advantage of the `listings` package to present it.
[[27]](https://en.wikibooks.org/wiki/LaTeX/Source_Code_Listings) gives a good overview
and [[28]](http://texblog.org/2011/06/11/latex-syntax-highlighting-examples/) presents a good code design.
In general, `breakatwhitespace=true` and a small `tabsize=x` must be recommended since the space is limited for documents.

I used the following code listing settings for my thesis:

{% gist 26c317c01cb8d7c4f78d %}

## Miscellaneous Simple Improvements

The last paragraph describes various simple enhancements for your thesis.
If you want to change the colors of your hyperlinks, e.g. to improve the readability, you just need to apply different settings [[29]](http://tex.stackexchange.com/questions/50747/options-for-appearance-of-links-in-hyperref/50754#50754).

    \usepackage[colorlinks, urlcolor=black, linkcolor=black, filecolor=black, citecolor=black]{hyperref}

To enhance the look of footnote cites and to indent more line citations, LaTeX settings must be overridden [[24]](   http://tex.stackexchange.com/questions/15952/layout-of-multiple-lines-footnotes):

    \makeatletter
    \renewcommand\@makefntext[1]{\leftskip=2em\hskip-2em\@makefnmark#1}
    \makeatother

Moreover, the `pifont` package provides nice looking Xs and ticks [[30]](https://www.ctan.org/pkg/pifont?lang=en). Thanks to [croeck](https://github.com/croeck) for the tip!
If you need to have a footnote at different places and to avoid duplicates,`footnotemark` can help you out
[[31]](http://tex.stackexchange.com/questions/35043/reference-different-places-to-the-same-footnote/35044#35044).
Line breaks in footnotes can be resolved for urls by `usepackage[hyphens]{url}` [[32]](http://tex.stackexchange.com/questions/23394/url-linebreak-in-footnote).
Additionally, the depth of chapter levels and their display in the table of content can be set by `setcounter{secnumdepth}{x}` and `setcounter{tocdepth}{x}`
[[33]](http://pleasemakeanote.blogspot.de/2010/06/how-to-activate-subsubsubsection-in.html).
Furthermore, spacing between values and units is simply realized by [[34]](http://tex.stackexchange.com/questions/20962/should-i-put-a-space-between-a-number-and-its-unit):

    \newcommand{\unit}[2]{#1$\mskip3mu$#2}

Tables can be a pain in the ass in LaTeX, but there are tools for a better table handling [[35]](http://tex.stackexchange.com/questions/49414/comprehensive-list-of-tools-that-simplify-the-generation-of-latex-tables). I used `Lyx` and it was absolutely fine with me.

Do you know missing essential packages others should consider? Just drop a comment and start the discussion :)
