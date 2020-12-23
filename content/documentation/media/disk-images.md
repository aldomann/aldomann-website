---
title: Disk images
toc: true
type: book
date: "2019-12-11T00:00:00Z"
draft: false

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 5
---

## Create a LiveUSB

To write the Live Install image to your USB, run the following command:

```bash
sudo dd bs=4M if=/path/to/antergos-x86_64.iso of=/dev/sdX && sync
```

## Mount an ISO image

To mount an ISO image on a virtual disk, run the following command:

```bash
udisksctl loop-setup -r -f image.iso
```
