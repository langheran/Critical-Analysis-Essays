---
title: Extraction of Parking Lot Structure From Aerial Image In Urban Areas
subtitle:
author: "[Nisim Hurst](mailto:langheran@gmail.com)"
date: Thursday 2 May 2019
abstract: ""
bibliography: Extraction-of-Parking-Lot-Structure-From-Aerial-Image-In-Urban-Areas/Extraction-of-Parking-Lot-Structure-From-Aerial-Image-In-Urban-Areas.bib
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

## Extraction of Parking Lot Structure From Aerial Image In Urban Areas

The article was written by [@koutaki2016extraction]. It was was cited [0](https://scholar.google.com/scholar?q=Extraction%20of%20Parking%20Lot%20Structure%20From%20Aerial%20Image%20In%20Urban%20Areas%20koutaki&hl=en&as_sdt=0&as_vis=1&oi=scholart&sa=X&ved=0ahUKEwiN67qBocbWAhXrjVQKHcX0BYwQgQMIMDAA) times according to Google Scholar. The task performed was detecting rectangular parking lot areas from aerial images. The metric for measuring performance is correctness., i.e. the ratio between the correctly extracted parking lots and the total extracted parking lots. They also use a % of detection metric, equal to the ratio between parking spots correctly extracted and the total real parking spots.

### Hypothesis

Combining vehicle detection with parking spot detection will be useful to detect rectangular parking lot structures.

### Evidence and Results

#### Dataset

For vehicle detection 2520 positive image patches of 14x32 pixels were used. Likewise, 4800 negative patches were used. For parking space detection a single image patch of 15x28 pixels was used.

For parking lot detection, 4 images of 2000x2000 pixels were used. Zoom level is 20cm per pixel.

The images were used to train a Haar-like detector in conjunction with an AdaBoost ensemble classifier.

#### Results

The parking lot rows were deduced using hierarchical grouping, starting with those parking spots that their centers are just one width of a parking spot apart.

The authors achieved 66.9% completeness detecting vehicles, 30.2% completeness for parking spot detection and correctness of 95% in rectangular parking lot extraction. In the later case, a completeness of 100% is assumed.

### Contribution

First, the paper thoroughly defines the geometric structure and appearance model of the parking lot.

Second, high resolution elevation data is used to remove buildings.  They combined a Digital Elevation Model and a Digital Surface Model with digital interpolation with the 4 urban zone images.

Third, a method for extracting those parking lots is proposed. This method is based on extracting both parking spaces and vehicle detection in parallel.

### Weaknesses
No comparison with other methods is shown. All the parking lots are assumed to be rectangular. A single angle of 90 degrees between the parking spot and the parking row is assumed.

### Future Work
For future work, the authors mention a shadow-resistant vehicle detection and to improve the single parking space extraction. Also, the authors mention that they wish to extend the algorithm to detect parking lots of arbitrary shape.


[Detection of vehicles](gotosumatra:5|32|613|G%3A%5CMy%20Drive%5CThesis%5C13Feb%5Fcomments%5Creferences%5CExtraction%20of%20Parking%20Lot%20Structure%20From%20Aerial%20Image%20In%20Urban%20Areas%2Epdf)
