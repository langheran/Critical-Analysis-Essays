---
title: Self-Supervised Aerial Image Analysis for Extracting Parking Lot Structure
subtitle:
author: "[Nisim Hurst](mailto:langheran@gmail.com)"
date: Thursday 2 May 2019
abstract: ""
bibliography: Self-Supervised-Aerial-Image-Analysis-for-Extracting-Parking-Lot-Structure/Self-Supervised-Aerial-Image-Analysis-for-Extracting-Parking-Lot-Structure.bib
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

## Self-Supervised Aerial Image Analysis for Extracting Parking Lot Structure
The article was written by Young-Woo Seo [@seo2009self]. It was was cited [19](https://scholar.google.com/scholar?client=ubuntu&channel=fs&oe=utf-8&pws=1&safe=active&um=1&ie=UTF-8&lr&cites=7197783101959033316) times according to Google Scholar. The task performed was estimating the parking lot structure from single parking spot detection using overall accuracy metric. The structure in this case is given by the global height, width, orientation and centroid location alignment.

### Hypothesis
A method that takes advantage of self-supervised low level (parking spot level) training will minimize human intervention while accurately estimate the parking lot structure.

### Evidence and Results

#### Dataset
Thirteen aerial images were collected from Google maps service. Those images have about 147 visible parking spots on average, adding up to 1912 parking spots in total.

#### Results
Evidence is presented in two parts. First, the overall accuracy of the initial estimates of the low-level line clustering and parking blocks method with their correspondence false positive and false negative rates. A false positive is considered more problematic because it would guide an autonomous robot to drive in unsafe places.

Then, three self-supervised classifiers are evaluated, namely: 1. Support Vector Machines, 2. Eigenspots and 3. Pairwise Markov Random Fields (with GMM). A fourth model combining Eigenspots and SVMs is also included in the test battery. Their results are presented contrasting the results obtained by training using the canonical parking spots alone and training by first enriching the dataset with self-supervised sample generation.

### Contribution
The main contribution of the paper is the comparison of the self-supervised approach vs the supervised approach through several machine learning models. 

A second contribution is a serial method that consist of the following high level steps:

1. Generate the parking spot global size parameters.
2. Generate canonical parking spots templates.
3. Generate initial parking spot estimates.
4. Calculate global distances between the parking spots.
5. Interpolate and extrapolate parking spot centroids in a single row.
6. Filter the hypothesis using the templates for self-supervised classifiers.

### Weaknesses
The angle between the parking spots and the parking block is assumed fixed to 90 degrees.
Also, distances that define the parking row structure and individual parking spot parameters are calculated globally. 

### Future Work
The authors propose using more machine learning trainable models that incorporate prior information to get a conclusive idea of the accuracy gain by using the self-supervised approach for this task.  
Histogram of Oriented Gradients is also proposed to extract more sophisticated feature representations.
