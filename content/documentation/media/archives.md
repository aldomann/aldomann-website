---
title: Archives
toc: true
type: book
date: "2019-12-10T00:00:00Z"
draft: false

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 4
---

## Compress each file in a different 7-Zip archive

```bash
for X in *; do 7z a -t7z -mx9 "$X".7z "$X"; done
```

## Compress each folder in a different ZIP archive

```bash
for i in */; do zip -r "${i%/}.zip" "$i"; done
```
