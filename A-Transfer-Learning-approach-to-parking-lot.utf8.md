---
title: A Transfer Learning approach to parking lot
subtitle:
author: "[Nisim Hurst](mailto:langheran@gmail.com)"
date: Thursday 2 May 2019
abstract: ""
bibliography: A-Transfer-Learning-approach-to-parking-lot/A-Transfer-Learning-approach-to-parking-lot.bib
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

## A Transfer Learning Approach to Parking Lot

The article was written by [@8085049]. It was was cited [0](https://scholar.google.com/scholar?hl=en&as_sdt=0%2C5&as_vis=1&q=A+Transfer+Learning+approach+to+parking+lot+Cisek&btnG=) times according to Google Scholar. The task performed was aerial patch imagery classification using the top 1 error rate and overall accuracy. The main focus of this paper is to compare a CNN with transfer learning based on the AlexNet network and a CNN with weights initialized from scratch.

### Hypothesis

Classification accuracy over aerial parking lot patches can be improved by using transfer learning. 

### Evidence and Results

#### Dataset

The images were obtained from the New York State GIS Clearinghouse. 12,000 image patches of 60x60 pixels with an overlapping of 30 pixels, i.e. there were just 8,000 or less completely different patches to classify. These were used both for training and validation. The target class is either *background*, *parking lot* or *none*.

#### Evidence

The authors tested 2 nets with transfer learning, namely LeNet and AlexNet. The layer architecture was left untouched. Just the learning rate.

### Contribution

First, the article provides solid evidence that neural networks can be applied to classify parking lot patches.

Second, the article compares performance gains by using transfer learning in two different convolutional network architectures. The dataset used for transfer learning was ILSVRC 2012. A 10.7% overall accuracy improvement was gained by using transfer learning.

### Weaknesses

The classification is applied to image patches of arbitrary size, i.e. 60x60 pixels each overlapping by 30 pixels (50%).  This patch size limits the features that can be learned in the convolutional layers due to the imposed padding.

Also, there is no segmentation, just classification of these image patches of fixed resolution and altitude. Partial occlusions are not considered neither.

### Future Work

The authors mention that other CNNs must be tested to establish a more conclusive relation between domain and the usefulness of transfer learning.
