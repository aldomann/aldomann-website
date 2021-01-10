---
title: Biodose Tools
summary: Shiny App for biological dosimetry laboratories.
tags: [biology, r-package]
date: "2019-10-12T00:00:00Z"

# Optional external URL for project (replaces project detail page).
external_link: ""

links:
- icon: github
  icon_pack: fab
  name: Code
  url: https://github.com/biodosetools-team/biodosetools/
- icon: box
  icon_pack: fas
  name: pkgdown
  url: https://biodosetools-team.github.io/biodosetools/
- icon: book
  icon_pack: fas
  name: Documentation
  url: https://biodosetools-team.github.io/documentation/
url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---

{{% badges %}}
  [![lifecycle](https://img.shields.io/badge/lifecycle-maturing-blue.svg)](https://www.tidyverse.org/lifecycle/#maturing)
  [![CRAN\_Status\_Badge](https://www.r-pkg.org/badges/version/biodosetools)](https://cran.r-project.org/package=biodosetools)
  [![pkgdown WorkflowStatus](https://github.com/biodosetools-team/biodosetools/workflows/pkgdown/badge.svg)](https://biodosetools-team.github.io/biodosetools/)
{{% /badges %}}

This project is an app to be used by biological dosimetry laboratories. Biodose Tools is an open source project that aims to be a tool to perform all different tests and calculations needed. The app is developed using the [R](https://www.r-project.org/about.html) programming language and [Shiny](https://shiny.rstudio.com) as a framework to offer an online, easy-to-use solution. Although the intention is to provide the application as a website, all R routines are available as an R package, which can be downloaded for improvement or personal use.

We also aim to clarify and explain the tests used and to propose those considered most appropriate. Each laboratory in its routine work should choose the optimum method, but the project aims to reach a consensus that will help us in case of mutual assistance or intercomparisons.

The project is initially developed by [RENEB](http://www.reneb.net) association, but contributions are always welcome.

## Installation

<!-- You can install the released version of <package> from [CRAN](https://CRAN.R-project.org) with: -->
<!-- ``` r -->
<!-- install.packages("biodosetools") -->
<!-- ``` -->
<!-- And  -->

The development version can be installed from
[GitHub](https://github.com/) with:

``` r
devtools::install_github("biodosetools-team/biodosetools")
```

<!-- ## Examples -->

## Citation

If you use data, results or conclusion from this work, please cite:

> A. Hernández, D. Endesfelder, J. Einbeck, P. Puig, A. Benadjaoud, M.
> Higueras, E. Ainsbury, G. Gruel, U. Kulka, L. Barrios & J. F.
> Barquinero (2020). Biodose Tools: An R Shiny Application for
> Biological Dosimetry. URL
> <https://biodosetools-team.github.io/biodosetools/>

A BibTeX entry for LaTeX users is:

``` bib
@Unpublished{,
  note = {Manuscript under construction},
  author = {Alfredo Hern{'{a}}ndez and David Endesfelder and Jochen Einbeck and Pere Puig and Amine Benadjaoud and Manuel Higueras and Elizabeth Ainsbury and Ga{"{e}}tan Gruel and Ulrike Kulka and Lleonard Barrios and Joan Francesc Barquinero},
  title = {Biodose Tools: An R Shiny Application for Biological Dosimetry},
  year = {2020},
  url = {https://biodosetools-team.github.io/biodosetools/},
}
```
