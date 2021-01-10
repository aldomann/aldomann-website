---
title: neuronsim
summary: Simulate the dynamics of neuronal ensembles.
tags: [biology, r-package]
date: "2020-11-20T00:00:00Z"

# Optional external URL for project (replaces project detail page).
external_link: ""

links:
- icon: github
  icon_pack: fab
  name: Code
  url: https://github.com/aldomann/neuronsim/
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
{{% /badges %}}

The goal of `{neuronsim}` is to simulate the dynamics of neuronal ensembles using the model of FREs and QIF neurons.

## Installation

The development version can be installed from [GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("aldomann/neuronsim")
```

## Examples

The macroscopic dynamics of neuronal ensembles can be described by solving the firing-rate equations (FREs):

``` r
library(neuronsim)

fre_output <- solve_fre(
  params = c(delta = 1, etabar = -2.5, J = 10.5),
  init_state = c(r = 0, v = -2),
  times = seq(from = -10, to = 80, by = 0.01),
  input = sin_input(t, current = 3, frequency = pi/20),
  method = "rk4"
)
```

To plot the macroscopic dynamics described by the FREs we can run

``` r
plot_macro_dynamics(fre_output)
```

{{< figure src="sin_macro_dynamics-1.png" lightbox="false" class="noshadow" >}}
