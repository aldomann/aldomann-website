---
title: "Override GitHub Linguist with gitattributes files"
subtitle: ""
summary: "Linguist is the library used on GitHub.com to detect blob languages, ignore binary or vendored files, suppress generated files in diffs, and generate language breakdown graphs."
authors: [admin]

tags: [programming]
categories: [tech]
projects: []

date: "2019-12-29T00:00:00Z"
lastmod: "2019-12-29T00:00:00Z"
featured: false
draft: true

image:
  caption: ""
  focal_point: ""
  preview_only: true
---

[Linguist](https://github.com/github/linguist) is the library used on GitHub.com to detect blob languages, ignore binary or vendored files, suppress generated files in diffs, and generate language breakdown graphs.

Linguist takes the list of languages it knows from [`languages.yml`](https://github.com/github/linguist/blob/master/lib/linguist/languages.yml) and uses a number of methods to try and determine the language used by each file, and the overall repository breakdown.

## Linguistic overrides

- https://github.com/github/linguist#overrides
- https://git-scm.com/docs/gitattributes

## Examples

- https://github.com/aldomann/tropical-cyclones-plus
