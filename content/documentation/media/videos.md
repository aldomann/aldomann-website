---
title: Videos
toc: true
type: book
date: "2019-12-10T00:00:00Z"
draft: false

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 4
---

## Remove subtitles from MKV

Assume we have `input.mkv` with 3 subtitle tracks. The following command removes subtitle track 2 by copying tracks 1 & 3 from `input.mkv` and saving it to `output.mkv`:

```bash
mkvmerge -o output.mkv --subtitle-tracks 1,3 input.mkv
```
