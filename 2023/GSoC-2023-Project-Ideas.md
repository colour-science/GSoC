# GSoC 2023 - Project Ideas

## Colour Science for Python

[Colour](https://github.com/colour-science/colour) is an open-source [Python](https://www.python.org/) package providing a comprehensive number of
algorithms and datasets for colour science.

It is freely available under the [New BSD License](https://opensource.org/licenses/BSD-3-Clause) terms.

## Table of Contents <!-- omit in toc -->

- [GSoC 2023 - Project Ideas](#gsoc-2023---project-ideas)
  - [Colour Science for Python](#colour-science-for-python)
  - [Mentors](#mentors)
  - [Project Ideas](#project-ideas)
    - [*Implement Support for CxF - Color Exchange Format*](#implement-support-for-cxf---color-exchange-format)
      - [Abstract](#abstract)
      - [Technical Details](#technical-details)
      - [Helpful Experience](#helpful-experience)
      - [First Steps](#first-steps)

## Mentors

- [Thomas Mansencal](https://github.com/KelSolaar)

## Project Ideas

### *Implement Support for CxF - Color Exchange Format*

#### Abstract

Developed by [X-Rite](https://www.xrite.com), the Color Exchange Format (CxF)
is an open standard designed for the communication and exchange of colour
information. The standard can be extended on per-application basis as required.
Colour would benefit from a CxF parser to exchange data with digital industry
software such as that from X-Rite.

| **Intensity** | **Priority** | **Involves**                                                                      | **Mentors**                                      |
|---------------|--------------|-----------------------------------------------------------------------------------|--------------------------------------------------|
| Moderate      | High         | Implementing support for CxF and learning how to write a parser for an XML schema | [Thomas Mansencal](https://github.com/KelSolaar) |

#### Technical Details

CxF support requires a custom parser for the
[Extensible Markup Language (XML)](https://en.wikipedia.org/wiki/XML) schema
defined by the standard schema. The following resources are available:

- [CxF Main Page](https://www.xrite.com/categories/digital-color-standards/color-exchange-format-cxf)
- [CxF Standard](https://www.xrite.com/-/media/xrite/files/literature/misc/c/cxf_standard_en.pdf)
- [CxF Schema Overview](https://www.xrite.com/-/media/xrite/files/literature/misc/c/cxf3_schema_overview_en.pdf)
- [Color Communication with CxF (Video)](https://vimeo.com/138970501)

#### Helpful Experience

- Colour science knowledge
- Knowledge of [ElementTree](https://docs.python.org/3/library/xml.etree.elementtree.html), [lxml](https://lxml.de) and [xmlschema](https://xmlschema.readthedocs.io).
- Basic knowledge of Colour

#### First Steps

- Setup the [development environment](https://www.colour-science.org/contributing/#contributing-code)
- Study the CxF standard and assess with the mentors the scope of implementation
- Study the `colour.io` sub-package
- Investigate the best approach to write the parser, e.g. is `ElementTree` enough or does `lxml` and `xmlschema` provide solid benefits?
- Implement the agreed standard scope
  