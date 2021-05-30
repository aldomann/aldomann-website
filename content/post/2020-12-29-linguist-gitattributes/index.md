---
title: "Override GitHub Linguist with gitattributes files"
subtitle: ""
summary: "Linguist is the library used on GitHub.com to detect blob languages, ignore binary or vendored files, suppress generated files in diffs, and generate language breakdown graphs."
authors: [admin]

tags: [programming]
categories: [tech]
projects: []

date: "2020-12-29T00:00:00Z"
lastmod: "2020-12-29T00:00:00Z"
featured: false
draft: false

image:
  caption: ""
  focal_point: ""
  preview_only: true
---

[Linguist](https://github.com/github/linguist) is, in short, the library used on GitHub to detect blob languages and generate language breakdown graphs. It takes the list of languages it knows from [`languages.yml`](https://github.com/github/linguist/blob/master/lib/linguist/languages.yml) and uses a number of methods to try and determine the language used by each file, and the overall repository breakdown.

## The issue

Let's consider the example below. The repository in question is an **R** project with some additional C++ and Mathematica scripts, but most importantly the repository also contains the source **LaTeX** files to build a report. Having a look at the language breakdown graph we would guess it's a TeX/LaTeX project.


{{< figure src="linguist-before.png" title="Original language breakdown graph" lightbox="true" width=40% >}}

Linguist is simply doing its job, but in this case it's inflating the project's TeX stats and causing it to be erroneously[^fn1] labeled.

The way to "correct" this is to use a [`.gitattributes`](https://git-scm.com/docs/gitattributes) file to [override Linguist's calculations](https://github.com/github/linguist#overrides).

## Linguist overrides

Linguist supports a number of different custom override strategies for language definitions and file paths. However, we are interested in overriding the `linguist-vendored` attributes.

In particular, in the example above, we can use the `linguist-vendored` attribute to vendor the `tex` path:

```txt
tex/* linguist-vendored
```

Below we can see the language breakdown graph correctly shows that the repository is mainly an R project.

{{< figure src="linguist-after.png" title="Corrected language breakdown graph" lightbox="true" width=40% >}}

## Additional examples

After learning about Linguist overrides, I've been playing around with some use cases for my projects and I've come up with a couple of example `.gitattributes` files that could be handy in different scenarios.

### R Markdown notebooks

```txt
*.Rmd linguist-language=R
*.nb.html linguist-vendored
```

Note that the first line may overinflate your R stats, as the percentages are calculated based on the bytes of code for each language. Feel free to delete it or comment it.

### Hugo websites

```txt
themes/* linguist-vendored
```

### {xaringan} presentations

```txt
slides/libs/* linguist-vendored
```

[^fn1]: Understandably, this may not be a problem to some people. However, I think there's a strong case to made about correctly labelling your repositories, as GitHub is increasingly being used as a way to show your portfolio.
