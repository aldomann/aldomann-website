---
title: Paper Extra Icons
summary: Custom icons for Paper Icon Theme by [Sam Hewitt](http://snwh.org/).
tags: [design]
date: "2015-11-19T00:00:00Z"
lastmod: "2018-09-24T00:00:00Z"

# Optional external URL for project (replaces project detail page).
external_link: ""

image:
  preview_only: true

links:
- icon: github
  icon_pack: fab
  name: Code
  url: https://github.com/aldomann/paper-extra-icons/
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
  [![Made with Inkscape](https://img.shields.io/badge/made_with-inkscape-yellow.svg)](https://creativecommons.org/licenses/by-sa/4.0/)
  [![LGPL 3 License](https://img.shields.io/badge/license-LGPL_3-blue)](https://www.gnu.org/licenses/lgpl-3.0.en.html)
{{% /badges %}}

Custom icons for Paper Icon Theme of the [Paper Project](https://snwh.org/paper) made by [Sam Hewitt](http://snwh.org/).

{{% badges %}}
  ![](https://raw.githubusercontent.com/aldomann/paper-extra-icons/master/Paper/48x48/apps/vineyard.png)
  ![](https://raw.githubusercontent.com/aldomann/paper-extra-icons/master/Paper/48x48/apps/mega.png)
  ![](https://raw.githubusercontent.com/aldomann/paper-extra-icons/master/Paper/48x48/emblems/mega-synced.png)
  ![](https://raw.githubusercontent.com/aldomann/paper-extra-icons/master/Paper/48x48/emblems/mega-pending.png)
  ![](https://raw.githubusercontent.com/aldomann/paper-extra-icons/master/Paper/48x48/emblems/mega-syncing.png)
  ![](https://raw.githubusercontent.com/aldomann/paper-extra-icons/master/Paper/48x48/mimetypes/application-mathematica.png)
  ![](https://raw.githubusercontent.com/aldomann/paper-extra-icons/master/Paper/48x48/mimetypes/text-x-matlab.png)
  ![](https://raw.githubusercontent.com/aldomann/paper-extra-icons/master/Paper/48x48/mimetypes/text-x-python3.png)
  ![](https://raw.githubusercontent.com/aldomann/paper-extra-icons/master/Paper/48x48/mimetypes/text-x-r-markdown.png)
  ![](https://raw.githubusercontent.com/aldomann/paper-extra-icons/master/Paper/48x48/mimetypes/application-x-r-project.png)
  ![](https://raw.githubusercontent.com/aldomann/paper-extra-icons/master/Paper/48x48/mimetypes/application-epub+zip.png)
  ![](https://raw.githubusercontent.com/aldomann/paper-extra-icons/master/Paper/48x48/mimetypes/application-x-mobipocket-ebook.png)
  ![](https://raw.githubusercontent.com/aldomann/paper-extra-icons/master/Paper/48x48/mimetypes/application-vnd.adobe.adept+xml.png)
  ![](https://raw.githubusercontent.com/aldomann/paper-extra-icons/master/Paper/48x48/mimetypes/text-x-tex.png)
  ![](https://raw.githubusercontent.com/aldomann/paper-extra-icons/master/Paper/48x48/mimetypes/text-x-bibtex.png)
{{% /badges %}}

Paper is a free culture icon theme by Sam Hewitt and is licenced under the terms of the [Creative Commons Attribution-Share Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/), unless otherwise specified.

## Downloading the original Icon Theme

The original source for Paper Icon Theme can be found [here](https://github.com/snwh/paper-icon-theme). You can clone the latest version from the git repository:

	git clone https://github.com/snwh/paper-icon-theme.git

## Using the Source

There are scripts to simplify the rendering process; to run them (and edit icons) you will need:

 * inkscape
 * python3
 * gtk-engine-murrine (optional)

To render new icons from their source SVG files, run the following:

	python render-bitmaps.py

If it's throwing an error, the script may not be executable, try:

	chmod +x render-bitmaps.py

This script will look in the source directory `(../src/*)` and render the respective icons (provided there are changes).

## Installation

Simple, you just run the script from the root of the source folder:
```bash
./INSTALL
```
Keep in mind that you need to have the original Paper Icon Theme for some symbolic links to work.
