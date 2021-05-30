---
title: gitlogr
summary: An easy to get and process your Git commit history.
tags: [r-package]
date: "2019-12-13T00:00:00Z"
lastmod: "2021-05-29T00:21:28Z"

# Optional external URL for project (replaces project detail page).
external_link: ""

links:
- icon: github
  icon_pack: fab
  name: Code
  url: https://github.com/aldomann/gitlogr/
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
  [![CRAN\_Status\_Badge](https://www.r-pkg.org/badges/version/gitlogr)](https://cran.r-project.org/package=gitlogr)
  <!-- [![pkgdown Workflow Status](https://github.com/aldomann/gitlogr/workflows/pkgdown/badge.svg)](https://aldomann.github.io/gitlogr/) -->
{{% /badges %}}

`{gitlogr}` aims to provide a clean way to get your Git commit history and process it in R.

## Installation

The development version can be installed from [GitHub](https://github.com/) with:

```r
# install.packages("devtools")
devtools::install_github("aldomann/gitlogr")
```

## Examples

The main function, `get_history()`, allows to quickly parse the results of `git log` into an R data frame.

```r
gitlogr::get_history(from = "2021-02-01", to = "2021-02-28") %>%
  knitr::kable()
```

| date                | message                                                          |
|:--------------------|:-----------------------------------------------------------------|
| 2021-02-26 10:10:06 | Fixed message left trimming in get_git_commit_history() function |
| 2021-02-26 10:24:05 | Minor refactoring and proper usage of rlang::.data               |
| 2021-02-26 10:24:58 | Added clipboard parameter to get_git_commit_history() function   |
| 2021-02-26 10:25:36 | Added examples and badges to README file                         |
| 2021-02-26 10:25:46 | Updated documentation                                            |
| 2021-02-26 10:26:01 | Version bump to v1.1.2                                           |

The `count_commits()` function is a wrapper of `get_history()` that can be used to calculate the amount of commits done in a certain date range.

```r
gitlogr::count_commits(from = "2019-12-01", to = "2019-12-31")
#> [1] 9
```
