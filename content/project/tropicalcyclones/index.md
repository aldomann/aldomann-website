---
title: tropicalcyclones
summary: Parse and explore data from tropical-cyclone databases.
tags: [r-package]
date: "2020-03-08T00:00:00Z"

# Optional external URL for project (replaces project detail page).
external_link: ""

links:
- icon: github
  icon_pack: fab
  name: Code
  url: https://github.com/aldomann/tropicalcyclones/
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
  [![lifecycle](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://www.tidyverse.org/lifecycle/#experimental)
  [![CRAN\_Status\_Badge](https://www.r-pkg.org/badges/version/tropicalcyclones)](https://cran.r-project.org/package=tropicalcyclones)
  [![pkgdown Workflow Status](https://github.com/aldomann/tropicalcyclones/workflows/pkgdown/badge.svg)](https://aldomann.github.io/tropicalcyclones/)
{{% /badges %}}

Parse and explore data from several tropical-cyclone related databases, such as HURDAT2, HadISST1, and OISST.

## Installation

The development version can be installed from [GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("aldomann/tropicalcyclones")
```

## Examples

Since `read_hurdat2()` is powered by `readLines`, we can use any connection, such as

  - Local files.
  - Compressed files.
  - Remote URLs.

``` r
hurr_obs_natl <- tropicalcyclones::read_hurdat2("hurdat2-1851-2016-apr2017.txt")
```

``` r
hurr_obs_natl <- tropicalcyclones::read_hurdat2("https://www.aoml.noaa.gov/hrd/hurdat/hurdat2.html")
