---
title: "The Centrifuge Problem"
subtitle: ""
summary: "Linguist is the library used on GitHub.com to detect blob languages, ignore binary or vendored files, suppress generated files in diffs, and generate language breakdown graphs."
authors: [admin]

tags: [programming, mathematica]
categories: [science]
projects: []

date: "2021-06-01T00:00:00Z"
lastmod: "2021-06-01T00:00:00Z"
featured: false
draft: true

image:
  caption: ""
  focal_point: ""
  preview_only: true

links:
- icon: github
  icon_pack: fab
  name: Code
  url: https://github.com/aldomann/the-centrifuge-problem/
---

A while ago (almost 3 years ago, to be more exact) I watched a video on [Numberphile](https://www.youtube.com/channel/UCoxcjq-8xIDTYp3uz647V5A) where [Dr Holly Krieger](https://twitter.com/hollykrieger) presents the following problem.

> Given a centrifuge with $n$ holes, is it possible to balance $k$ test tubes?

{{< youtube-video id="7DHE8RnsCQ8" >}}

## Mathematical solution

On the video Dr Krieger goes over her thinking process, and some of the intuitive (and not so intuitive) ways of constructing solutions. Particularly, a solution is valid if and only if both the number of test tubes, $k$, and the number of empty spots, $n - k$, can be expressed as sums of prime factors of $n$.

The main takeaway, for me, is this problem can be thought of as finding the subset $S$, of the set $R$ of roots of a complex number $z$, such that their sum is zero:

$$
  \sum_{i = 1}^{k} s_{i} = 0,
  \quad \text{where} \\; s_{i} \in S \subseteq R,
  \quad \text{given} \\;
  R = \left\\{\eta\omega^{0}, \eta\omega^{1}, \eta\omega^{2}, \dots, \eta\omega^{n-1} \right\\}
  ,
$$

where $(\eta\omega^{j})^{n} = z$, $\forall j \in \left\\{ 0, 1, 2, \dots, n - 1 \right\\}$, $k \leq n \in \mathbb{Z}$, and $z \in \mathbb{C}$.

For simplicity, if we take $z = 1$, then the roots become of the form $1$, $\omega$, $\omega^{2}$, ..., $\omega^{n-1}$, with $\omega = e^{\frac{2\pi i}{n}}$. This is a fairly simple computational problem to solve if we brute force it, which is exactly what I did.

## Computational solution

As an exercise to refresh my Mathematica programming and graphing skills, I decided to solve this problem using [Wolfram Mathematica](https://www.wolfram.com/mathematica/).

The problem, from a computational point of view, can be divided into main the following problems:

- Find the set of roots, $R$.
- Find all possible subsets $S \subseteq R$.
- Check which subsets are valid solutions.

### Finding the roots

```mathematica
MyFindRoots[z_, n_] := Module[{roots, r, angle},
  roots = ConstantArray[0, n];
  For[k = 0, k < n, k++, {
    r := Abs[z],
    angle := Arg[z],
    r = r^(1 / n),
    roots[[k + 1]] = r * Exp[I * (angle + 2 * Pi * k)/n]
    }];
  roots
]
```

A much faster alternative to `MyFindRoots` would be to use the `Solve` function:

```mathematica
MyFindRootsNative[z_, n_] := Solve[x^n == z, x][[All, 1, 2]]
```

### Finding the valid subsets


### Reducing the solutions
