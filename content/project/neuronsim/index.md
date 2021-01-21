---
title: neuronsim
summary: Simulate the dynamics of neuronal ensembles.
tags: [biology, r-package]
date: "2020-11-20T00:00:00Z"
lastmod: "2021-01-21T00:16:00Z"

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
  [![CRAN\_Status\_Badge](https://www.r-pkg.org/badges/version/neuronsim)](https://cran.r-project.org/package=neuronsim)
  [![lifecycle](https://img.shields.io/badge/lifecycle-maturing-blue.svg)](https://www.tidyverse.org/lifecycle/#maturing)
{{% /badges %}}

The goal of `{neuronsim}` is to simulate the dynamics of neuronal ensembles using the model of FREs and QIF neurons.

## Installation

The development version can be installed from [GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("aldomann/neuronsim")
```

## Examples

```r
library(neuronsim)

init_state <- c(r = 0, v = -2)
params <- c(delta = 1, etabar = -5, J = 15)
times_seq <- seq(from = -10, to = 40, by = 0.001)
current <- constant_input(t, current = 3, t_start = 0, t_end = 30)
```

The macroscopic dynamics of neuronal ensembles can be described by solving the firing-rate equations (FREs):

```r
fre_output <- solve_fre(
  params = params,
  init_state = init_state,
  times = times_seq,
  input = current,
  method = "rk4"
)
```

The microscopic dynamics of neuronal ensembles can be described by running a QIF neurons simulation:

```r
qif_output <- simulate_qif(
  params = params,
  init_state = init_state,
  times = times_seq,
  input = current(times_seq)
)
```

To plot the macroscopic and microscopic dynamics of the ensemble we can run:

```{r sin-dynamics, fig.width=8, fig.height=4}
plot_dynamics(
  data = list(fre_output, qif_output$data),
  raster_data = qif_output$raster
)
```

{{< figure src="sin-dynamics-1.png" lightbox="false" class="noshadow" >}}
