---
title: A Method for Camera Vision Based Parking Spot Detection
subtitle:
author: "[Nisim Hurst](mailto:langheran@gmail.com)"
date: Thursday 2 May 2019
abstract: ""
bibliography: A-Method-for-Camera-Vision-Based-Parking-Spot-Detection/A-Method-for-Camera-Vision-Based-Parking-Spot-Detection.bib
urlcolor: blue
biblio-style: "authoryear" # "apalike" "apa" "authoryear"
link-citations: true
csl: ieee.csl
output:
  bookdown::pdf_document2:
    pandoc_args:
      - "--csl"
      - "ieee.csl"
      - "--metadata"
      - "link-citations"
      - "--filter"
      - "pandoc-eqnos"
    toc: no
    toc_depth: 5
    number_sections: no
    keep_tex: true
    citation_package: biblatex
#    includes:
#      before_body: ../doc-prefix.tex
header-includes: |
    \usepackage{float}
    \usepackage{graphicx}
    \usepackage{subfig}
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \usepackage{truncate}
    \renewcommand{\subsectionmark}[1]{\markright{#1}{}}
    \fancyhf{}
    \lhead{\small\truncate{400pt}{\rightmark}}
    \rhead{\small\hyperref[toc]{Table Of Contents}}
    \rfoot{Page \thepage}
    \usepackage{caption}
    \usepackage{listings}
    \usepackage{attachfile}
    \makeatletter\renewcommand*{\fps@figure}{H}\makeatother
    \usepackage{cleveref}

    \usepackage{xcolor}
    \definecolor{block-gray}{gray}{0.85}
    \usepackage{environ}
    \NewEnviron{quoteblock}
    {\colorbox{block-gray}{
    \parbox{\dimexpr\linewidth-2\fboxsep\relax}{
    \small\addtolength{\leftskip}{10mm}
    \addtolength{\rightskip}{10mm}
    \BODY}}
    }
    \renewcommand{\quote}{\quoteblock}
    \renewcommand{\endquote}{\endquoteblock}
    \ifdef{\printbibliography}{
       \defbibheading{subsubbibliography}[\refname]{\subsubsection*{#1}}
       \let\oldprintbibliography\printbibliography
       \renewcommand{\printbibliography}[1]{
          \phantomsection
          \addcontentsline{toc}{section}{References}
          \oldprintbibliography[title={References},heading=subsubbibliography]
          }
    }{

    }
#site: bookdown::bookdown_site
#documentclass: extarticle
#geometry: "left=1cm, right=1cm, top=2.5cm, bottom=2.5cm"
#fontsize: 17pt
#linestretch: 1.5
---
\label{toc}

## A Method for Camera Vision Based Parking Spot Detection

The article was written by [@Weis_2006]. It was was cited [3](https://scholar.google.com/scholar?cites=14395139259540139730&as_sdt=2005&sciodt=0,5&hl=en) times according to Google Scholar. The task performed was detecting parking spot behind a vehicle from its rear camera.

### Hypothesis

By using color for edge detection using a Kirsch filter it is possible to detect available parking spots.

### Evidence and Results
Four images show parking spot detection. The first shows a parking spot occluded by a car being detected. The second image shows a free parking spot being detected. The third and fourth images show rejections.

### Contribution
A first contribution is a thorough problem characterization of detecting a parking spot from a frontal camera. Two different parking spots poses are considered: perpendicular and parallel. 

The whole method is based in detecting the parking lines and then apply fixed rules to filter them over a semantic analysis. 

First, the authors pre-process the image to filter out colors and gray levels not belonging to classical parking lines. Then, the authors use a Kirsh filter to vectorize the lines. Finally, semantical filtering is applied.

### Weaknesses
No quantitative results are show, just a red overlay over the parking lines and a green frame over the surmised parking spot.

A range on the size of a parking spot, i.e. its height and width, is assumed.

### Future Work
Apply learning of some kind rather than assume fixed ranges.
