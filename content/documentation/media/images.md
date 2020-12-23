---
title: Images
toc: true
type: book
date: "2019-12-10T00:00:00Z"
draft: false

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 4
---

## Resize images

```bash
mogrify -resize x1920 *.jpg
mogrify -resize 320x240 *.png
mogrify -resize 50% *.png
mogrify -resize 320x240 *.jpg
```
