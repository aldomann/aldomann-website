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
draft: false

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

For simplicity, if we take $z = 1$, then the roots become of the form $1$, $\omega$, $\omega^{2}$, ..., $\omega^{n-1}$, with $\omega = e^{\frac{2\pi i}{n}}$. This is illustrated for $n = 5$ in the figure below.

{{< figure src="https://upload.wikimedia.org/wikipedia/commons/4/40/One5Root.svg" title="The 5th roots of unity (blue points) in the complex plane, from [Wikipedia](https://en.wikipedia.org/wiki/Root_of_unity)" lightbox=false class="noshadow" width="40%" >}}

Finding roots of unity ($z = 1$) and checking subsets that add up to zero is fairly simple computational problem to solve if we brute force it, which is exactly what I did.

## Computational solution

As an exercise to refresh my Mathematica programming and graphing skills, I decided to solve this problem using [Wolfram Mathematica](https://www.wolfram.com/mathematica/).

The problem, from a computational point of view, can be divided into main the following problems:

- Find the set of roots, $R$.
- Find all possible subsets $S \subseteq R$.
- Check which subsets are valid solutions.

### Finding the roots

Finding the $n$ roots of a complex number $z$ is a very easy task to do using a loop:

```mathematica
MyFindRoots[z_, n_] := Module[{roots, r, angle},
  roots = ConstantArray[0, n];
  For[k = 0, k < n, k++, {
    r = Abs[z],
    angle = Arg[z],
    r = r^(1 / n),
    roots[[k + 1]] = r * Exp[I * (angle + 2 * Pi * k) / n]
    }];
  roots
]
```

As an example, we can find the 5th roots of unity shown in the previous section:

```mathematica
MyFindRoots[1, 5]
```
```text
{1, E^((2 I Pi)/5), E^((
 4 I Pi)/5), E^(-((4 I Pi)/5)), E^(-((2 I Pi)/5))}
```

A native alternative to `MyFindRoots` would be to use the `Solve` function:

```mathematica
MyFindRootsNative[z_, n_] := Solve[x^n == z, x][[All, 1, 2]]
```

However, this function is slower in the range of $n$ we would solve the problem for (let me know if you find a centrifuge with 1000 holes):
```mathematica
Needs["GeneralUtilities`"]
f1 = MyFindRoots[1, #] &;
f2 = MyFindRootsNative[1, #] &;
BenchmarkPlot[{f1, f2}, # &, PowerRange[1, 1000], "IncludeFits" -> True]
```

{{< figure src="benchmark.png" title="Benchmarking results of `MyFindRoots` compared to `MyFindRootsNative`" lightbox=false class="noshadow" width="80%" >}}

For this reason, we would choose `MyFindRoots` over the `Solve`-powered `MyFindRootsNative` function.

### Finding the subsets

One of the awesome things about Mathematica is that operations in set theory are trivial. To get all subset $S \subseteq R$ we can run, for example,

```mathematica
RootsSetR := MyFindRoots[1, 4]
RootSubsetsS = Subsets[RootsSetR, Length[RootsSetR]]
```
which results in the list of all possible $2^{n}$ subsets:
```text
{{}, {1}, {I}, {-1}, {-I}, {1, I}, {1, -1}, {1, -I}, {I, -1}, {I, -I}, {-1, -I}, {1, I, -1}, {1, I, -I}, {1, -1, -I}, {I, -1, -I}, {1, I, -1, -I}}
```

### Checking valid subsets

The problem here will be, thus, checking if the solutions are valid. To calculate the sum of all elements of each subset $i$ of the family of subsets of $S$, we can simply do
```mathematica
RootSubsetsS[[7]]
Total[RootSubsetsS[[7]]]
```
```text
{1, -1}
0
```

This example shows that, for $n=4$, one particular valid solution would be {1, -1}, that is two holes opposite to each other.

Taking all this into account, a simple function to find all possible solutions can be the following:
```mathematica
FindCentrifugeSols[n_] := Module[{solutions, roots, subsets, subset, total, epsilon, i},
  roots = UsedFindRoots[1, n];
  subsets = Subsets[roots, n];
  epsilon = Power[10, -15];
  solutions = {};
  (*Main loop*)
  For[i = 1, i <= Length[subsets], i++, {
    subset = subsets[[i]],
    total = Total[subset],
    If[Abs[N[total]] < epsilon,
      solutions = Append[solutions, subset]
    ]
  }];
  (*Return*)
  {roots, solutions}
]
```

Let's see it action (note that it returns the set of roots $R$, and family of valid subsets $S$):
```mathematica
FindCentrifugeSols[4]
```
```text
{
  {-1, -I, I, 1},
  {{}, {-1, 1}, {-I, I}, {-1, -I, I, 1}}
}
```

To better visualise the solutions, I wrote a function[^fn1] to draw the centrifuge configurations:
```mathematica
DrawCentrifugeSols[4]
```

{{< figure src="sols_4_nonunique.png" title="Non-unique solutions for the Centrifuge Problem for $n=4$"lightbox=false class="noshadow" width="250px" >}}

An obvious thing to notice here is that for $k = 2$, the two found solutions are not unique under rotation. This may not seem like a big deal, but for larger values of $n$, the solution space is littered with non-unique solutions under rotation:

{{< figure src="sols_12_nonunique.png" title="Non-unique solutions for the Centrifuge Problem for $n=12$"lightbox=false class="noshadow" >}}

Here's where things get a bit more complicated.

### Reducing the solutions

Up to this point, we've already *solved* the Centrifuge Problem. However, we want to reduce the solutions to truly unique configurations of a centrifuge.

The gist of this step is that we need to rotate all solutions and compare them to each other to get rid of duplicated ones. To accomplish this, we will introduce a set of auxiliary functions:

- `RotateSol`.
- `SortSetClockwise`.
- `ClassifyCentrifugeSols`.

```mathematica
RotateSol[n_, k_, sol_] := sol * Exp[I * (2 * Pi * k) / n]
```

This function simply applies a rotation of $(2 \pi k)/n$ to a complex number. This is essential to reduce the found solutions to unique solutions under a rotation symmetry.

```mathematica
SortSetClockwise[set_] := Module[{angles, order},
  angles = Map[Arg, set];
  order = Ordering[angles, All, NumericalOrder];
  angles = angles[[order]];
  Map[Exp, I * Pi * Rationalize[N[angles] / Pi]]
]
```

This step is probably the most important one to minimise calculations. Since we'll be comparing solutions in set form as a whole, we need to make sure they follow a specific, deterministic structure.

```mathematica
ClassifyCentrifugeSols[n_] := Module[{MyMat, MyVect, roots, subsets, subset, epsilon, solutions, curr, next, i},
  solutions = FindCentrifugeSols[n];
  subsets = Sort[solutions[[2]]];
  roots = solutions[[1]];
  epsilon = Power[10, -15];
  MyMat = {};
  MyVect = {};
  (*Main loop*)
  For[i = 1, i <= Length[subsets], i++, {
    subset = subsets[[i]],
    curr = Length[subset];
    (*Check length of next element*)
    If[i + 1 <= Length[subsets],
      next = Length[subsets[[i + 1]]],
      next = 0
    ];
    (*Append subset to vector*)
    MyVect = Append[MyVect, SortSetClockwise[subset]];
    (*Append subsets to matrix*)
    If[next != Length[subset] && Length[MyVect] > 0,
      MyMat = Append[MyMat, {curr, MyVect}];
      MyVect = {};
    ];
  }];
  (*Return*)
  {roots, MyMat}
]
```

If we put all of this together, we can write the following function:
```mathematica
ReduceCentrifugeSols[n_] := Module[{Sols, SubSols, UniqueSubSols, UniqueSols, MyLength, permuteSolsBool, RotatedSol, RotatedSols, Sol, Add, element, i},
  Sols = ClassifyCentrifugeSols[n];
  MyLength = Length[Sols[[2]]];
  UniqueSols = {};
  (*Iterate over each subset size*)
  For[i = 1, i <= MyLength, i++,
    UniqueSubSols = {};
    SubSols = Sols[[2]][[i]][[2]];
    (*Loop over solution sub-space*)
    For[element = 1, element <= Length[SubSols], element++,
      RotatedSols = {};
      Sol = SubSols[[element]];
      Sol = SortSetClockwise[Sol];
      (*Rotate one solution*)
      For[k = 0, k < n, k++,
        RotatedSol = RotateSol[n, k, Sol];
        RotatedSol = SortSetClockwise[RotatedSol];
        RotatedSols = Append[RotatedSols, RotatedSol]
      ];
      (*Add to list of unique solutions*)
      If[Length[Intersection[UniqueSubSols, RotatedSols]] == 0,
        UniqueSubSols = Append[UniqueSubSols, Sol];
      ]
    ];
    UniqueSols = Append[UniqueSols, {Sols[[2]][[i]][[1]], UniqueSubSols}];
  ];
  (*Return*)
  {Sols[[1]], UniqueSols}
]
```

```mathematica
ReduceCentrifugeSols[4]
```
```text
{
  {-1, -I, I, 1},
  {{0, {{}}}, {2, {{1, -1}}}, {4, {{-I, 1, I, -1}}}}
}
```

Likewise, I wrote `DrawCentrifugeUniqueSols` to draw the solutions to `ReduceCentrifugeSols`:
```mathematica
DrawCentrifugeUniqueSols[4]
```

{{< figure src="sols_4_unique.png" title="Unique (under rotation) solutions for the Centrifuge Problem for $n=4$"lightbox=false class="noshadow" width="200px">}}

{{< figure src="sols_12_unique.png" title="Unique (under rotation) solutions for the Centrifuge Problem for $n=12$"lightbox=false class="noshadow" width="450px">}}

### Going further

One minor issue I've noticed with my `ReduceCentrifugeSols` method is that it doesn't reduce solutions that are the same under reflections. This is an issue I may address in the future, but for now I'm happy with my method.

[^fn1]: The full code can be found on https://github.com/aldomann/the-centrifuge-problem/.
