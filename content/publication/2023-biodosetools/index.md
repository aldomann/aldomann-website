---
title: "Biodose Tools: An R shiny Application for Biological Dosimetry"
authors:
  - admin
  - David Endesfelder
  - Jochen Einbeck
  - Pedro Puig
  - Mohamed Amine Benadjaoud
  - Manuel Higueras
  - Elizabeth Ainsbury
  - Gaëtan Gruel
  - Ursula Oestreicher
  - Leonardo Barrios
  - Joan Francesc Barquinero
# authors_short:
author_notes: []
date: "2023-02-02"
doi: "10.1080/09553002.2023.2176564"

# Schedule page publish date (NOT publication's date).
publishDate: "2023-02-19T00:00:00Z"

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["2"]

# Publication name and optional abbreviated publication name.
publication: "*International Journal of Radiation Biology*, 0(0), 1-13"
publication_short: ""

abstract: "
*Introduction*:
In the event of a radiological accident or incident, the aim of biological dosimetry is to convert the yield of a specific biomarker of exposure to ionizing radiation into an absorbed dose. Since the 1980s, various tools have been used to deal with the statistical procedures needed for biological dosimetry, and in general those who made several calculations for different biomarkers were based on closed source software. Here we present a new open source program, Biodose Tools, that has been developed under the umbrella of RENEB (Running the European Network of Biological and retrospective Physical dosimetry).


*Materials and methods*:
The application has been developed using the R programming language and the shiny package as a framework to create a user-friendly online solution. Since no unique method exists for the different mathematical processes, several meetings and periodic correspondence were held in order to reach a consensus on the solutions to be implemented.


*Results*:
The current version 3.6.1 supports dose-effect fitting for dicentric and translocation assay. For dose estimation Biodose Tools implements those methods indicated in international guidelines and a specific method to assess heterogeneous exposures. The app can include information on the irradiation conditions to generate the calibration curve. Also, in the dose estimate, information about the accident can be included as well as the explanation of the results obtained. Because the app allows generating a report in various formats, it allows traceability of each biological dosimetry study carried out. The app has been used globally in different exercises and training, which has made it possible to find errors and improve the app itself. There are some features that still need consensus, such as curve fitting and dose estimation using micronucleus analysis. It is also planned to include a package dedicated to interlaboratory comparisons and the incorporation of Bayesian methods for dose estimation.


*Conclusion*:
Biodose Tools provides an open-source solution for biological dosimetry laboratories. The consensus reached helps to harmonize the way in which uncertainties are calculated. In addition, because each laboratory can download and customize the app’s source code, it offers a platform to integrate new features.
"

# Summary. An optional shortened abstract.
summary: ""

tags:
- biology
featured: false

links:
- name: 'YouTube'
  url: 'https://www.youtube.com/@biodosetools'
url_pdf: publication/2023-biodosetools/biodosetools_2023.pdf
url_code: 'https://github.com/biodosetools-team/biodosetools/'
url_dataset: ''
url_poster: ''
url_project: ''
url_slides: ''
url_source: ''
url_video: ''

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
image:
  caption: 'Mockup illustrating Biodose Tools’ color coding to create an intuitive visual organization of the user interface.'
  focal_point: ""
  preview_only: false

# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `internal-project` references `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
projects: [biodose-tools]

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
slides: ""
---
