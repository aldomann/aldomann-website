---
title: Installing Git
toc: true
type: book
date: "2019-12-14T00:00:00Z"
lastmod: "2020-12-23T00:00:00Z"
draft: false

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1
---

## On GNU/Linux

On any decent Linux distribution, Git should be installed by default (yeah, looking at you Ubuntu). If that’s not the case, you can just install it from your terminal.

### Debian/Ubuntu derivatives

```bash
sudo apt install git
```

### Arch Linux

```bash
sudo pacman -S git
```

### Fedora

```bash
sudo dnf install git
```

## On mac OS

To have `git` (and `gcc`, and any basic developer tool), you must have XCode on your system, so just head to the App Store and install it. . Expect to waste half your afternoon, as it is around 6 GB to download, and then it needs to be installed.

If you won't use XCode, it's recommended to just install the XCode Command Line Tools by running:

```bash
xcode-select install
```

Alternatively, if you use [Homebrew](https://brew.sh/) you can install Git by running:

```bash
brew install git
```
