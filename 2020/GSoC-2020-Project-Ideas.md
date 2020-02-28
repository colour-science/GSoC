# GSoC 2020 - Project Ideas

## Colour Science for Python

[Colour](https://github.com/colour-science/colour) is an open-source [Python](https://www.python.org/) package providing a comprehensive number of
algorithms and datasets for colour science.

It is freely available under the [New BSD License](https://opensource.org/licenses/BSD-3-Clause) terms.

## Table of Contents <!-- omit in toc -->

- [Colour Science for Python](#colour-science-for-python)
- [Mentors](#mentors)
- [Project Ideas](#project-ideas)
  - [*The Need for Speed*](#the-need-for-speed)
  - [*New Colour Appearance Models*](#new-colour-appearance-models)
  - [*New Colour Quality Metrics*](#new-colour-quality-metrics)
  - [*New Spectral Upsampling Methods*](#new-spectral-upsampling-methods)
  - [*LUT IO Improvements*](#lut-io-improvements)

## Mentors

- [Michael Mauderer](https://github.com/MichaelMauderer)
- [Thomas Mansencal](https://github.com/KelSolaar)

## Project Ideas

### *The Need for Speed*

#### Abstract

Most of Colour's code is vectorised through [Numpy](https://numpy.org/), while
trying to be as faithful as possible to the scientific publications implemented.
Execution speed has never been the primary focus for the development, however,
it is often an important factor to consider when adopting a library thus we
would like to improve the general performance of Colour.

| **Intensity** | **Priority** | **Involves** | **Mentors** |
| --- | --- | --- | --- |
| Moderate/Hard | Medium | Implementing a benchmarking suite, investigating usage of [CuPy](https://cupy.chainer.org/), [Bohrium](https://github.com/bh107/bohrium) or any relevant GPU backend (e.g., OpenCL), measuring performance, and finally based on the initial investigation, improving speed in image processing hotspots. | [Michael Mauderer](https://github.com/MichaelMauderer), [Thomas Mansencal](https://github.com/KelSolaar) |

#### Technical Details

Performance measurements require the creation of a benchmarking suite that can
quantify the improvements. [Airspeed Velocity (ASV)](https://asv.readthedocs.io/)
is a tool for benchmarking Python packages, used by
[scikit-image](https://scikit-image.org/docs/dev/contribute.html#benchmarks)
and would be a suitable candidate. The benchmark should ensure that basic
colour conversions (e.g., CIE XYZ to CIE Lab) run with a good performance when
processing large images, e.g. HD1080, UHD resolution. At this stage, we are
interested in trying out drop-in improvements like CuPy and Bohrium: they offer
an almost drop-in Numpy like API. They might provide significant performance
improvement to the whole library for a minimal amount of work. We are also open
to evaluating manual improvements su as re-implementing algorithms directly
with Cython, Rust or OpenCL.

#### Helpful Experience

- Experience with testing or benchmarking numerical code
- Knowledge of Numpy, Scipy, vectorisation and GPU programming
- Basic knowledge of Colour

#### First Steps

- Investigate [Airspeed Velocity](https://asv.readthedocs.io/)
- Design and implement a benchmarking suite for Colour
- Discuss with the Colour developers about the preferred transformations to
  measure the performance of and benchmark them
- Investigate possible optimizations and GPU backends

### *New Colour Appearance Models*

#### Abstract

Colour implements Colour Appearance Models (CAM), most notably Hunt, CIECAM02
and CAM16. More models would be useful for research purposes, especially for
High Dynamic Range (HDR) image processing.

| **Intensity** | **Priority** | **Involves** | **Mentors** |
| --- | --- | --- | --- |
| Moderate | High | Implement new Colour Appearance Models. | [Michael Mauderer](https://github.com/MichaelMauderer), [Thomas Mansencal](https://github.com/KelSolaar) |

#### Technical Details

[Colour appearance modeling](https://en.wikipedia.org/wiki/Color_appearance_model)
is critical to the prediction of colours under different viewing conditions.
The current model recommended by the [CIE](http://cie.co.at/) is
[CIECAM02](https://en.wikipedia.org/wiki/CIECAM02) and is not designed to
process HDR imagery. [Sadfar et al. (2018)](https://doi.org/10.2352/ISSN.2169-2629.2018.26.96)
proposed a new CAM based on JzAzBz colourspace with support for HDR imagery.
Other CAMs such as [iCAM06](https://doi.org/10.1016/j.jvcir.2007.06.003),
[Kim, Weyrich and Kautz (2009)](https://dl.acm.org/doi/abs/10.1145/1531326.1531333),
the [Comprehensive CAM](https://doi.org/10.1002/col.22078), and
[CAM15u](https://doi.org/10.1364/OE.23.012045) are also prime candidates for
addition.

#### Helpful Experience

- Colour science and colour appearance modeling
- Ability to read scientific publications
- Knowledge of Numpy and Scipy
- Basic knowledge of Colour

#### First Steps

- Study the `colour.appearance` sub-package
- Implement Sadfar et al. (2018) CAM forward and reverse transformations
- Implement the remaining CAMs in the preferred following order:
    - iCAM06
    - Kim, Weyrich and Kautz (2009)
    - Comprehensive CAM
    - CAM15u

### *New Colour Quality Metrics*

#### Abstract

The CIE current recommended method for measuring Colour Quality is the
[CIE 2017 Colour Fidelity Index (CFI 2017)](http://cie.co.at/publications/cie-2017-colour-fidelity-index-accurate-scientific-use).
It supersedes the [Colour Rendering Index (CRI)](https://en.wikipedia.org/wiki/Color_rendering_index)
and should be implemented in Colour along with the related
[IES TM-30-15](http://www.ies.org/store/product/ies-method-for-evaluating-light-source-color-rendition-3368.cfm).

| **Intensity** | **Priority** | **Involves** | **Mentors** |
| --- | --- | --- | --- |
| Moderate | High | Implement new Colour Quality Metrics. | [Michael Mauderer](https://github.com/MichaelMauderer), [Thomas Mansencal](https://github.com/KelSolaar) |

#### Technical Details

Colour implements the SSI, CRI and CQS quality metrics, the two latter have
been superseded with IES TM-30-15 and CFI 2017. To bring Colour up to latest
standards, those two metrics need to be implemented. Leveraging that those new
metrics, an exhaustive light quality report using new plotting definitions
should be implemented.

#### Helpful Experience

- Colour science and colour quality
- Ability to read scientific publications
- Knowledge of Numpy and Scipy
- Basic knowledge of Colour

#### First Steps

- Study the `colour.quality` sub-package
- Implement IES TM-30-15
- Implement CFI 2017

### *New Spectral Upsampling Methods*

Spectral upsampling (or recovery) is the conversion of CIE XYZ tristimulus values
(or RGB values) to the spectral domain. Colour already implements
[Smith (1999)](https://doi.org/10.1080/10867651.1999.10487511) and
[Meng et al. (2015)](https://doi.org/10.1111/cgf.12676) methods and would
benefit from the latest research algorithms.

#### Abstract

| **Intensity** | **Priority** | **Involves** | **Mentors** |
| --- | --- | --- | --- |
| Moderate | High | Implement new Spectral Upsampling Methods. | [Michael Mauderer](https://github.com/MichaelMauderer), [Thomas Mansencal](https://github.com/KelSolaar) |

#### Technical Details

Spectral representation and processing is critical to faithfully model
metamerism and accurately produce radiometric quantities. Unfortunately,
spectral data is not widespread and spectral imagery even more so, while
imposing huge acquisition and processing constraints. Spectral upsampling is
used in modern research rendering systems such as [PBRT](https://github.com/mmp/pbrt-v3)
and [Mitsuba](https://www.mitsuba-renderer.org/) or production renderers such
as [Manuka](https://www.wetafx.co.nz/research-and-tech/technology/manuka/) to
convert input colours and textures to the spectral domain. Research is active
around this topic with recent publications from
[Otsu et al. (2018)](http://lightmetrica.org/h-otsu/project/rgb2spec/),
[Jakob and Hanika (2019)](http://rgl.epfl.ch/publications/Jakob2019Spectral),
[Mallett and Yuksel (2019)](https://geometrian.com/data/research/spectral-primaries/EGSR2019_SpectralPrimaryDecomposition.pdf)
or [Peters et al. (2019)](https://doi.org/10.1145/3306346.3322964). Colour
would highly benefit from having those algorithms implemented.

#### Helpful Experience

- Colour science and spectral rendering
- Experience in numerical optimization
- Knowledge of Numpy and Scipy
- Basic knowledge of Colour

#### First Steps

- Research the latest publications and literature on spectral upsampling
- Study the `colour.recovery` sub-package
- Implement support in priority for Otsu et al. (2018) and Jakob and Hanika (2019)
  methods
- Implement support for Mallett and Yuksel (2019) and Peters et al. (2019) in
  a second time, and if only nothing significant was highlighted in recent
  research.

### *LUT IO Improvements*

#### Abstract

| **Intensity** | **Priority** | **Involves** | **Mentors** |
| --- | --- | --- | --- |
| Moderate | High | Improve LUT Input/Output Capabilities. | [Michael Mauderer](https://github.com/MichaelMauderer), [Thomas Mansencal](https://github.com/KelSolaar) |

#### Technical Details

Colour offers good support for lookup table (LUT) input and output but [several
features could be implemented](https://github.com/colour-science/colour/issues/500)
to improve the current capabilities:

- Support for LUT inversion
- [CLF 3](http://j.mp/S-2014-006) support
- Implement a Log2 shaper as per OCIO reference
- Implement an ExponentWithLinear function
- Implement a generic parameterised camera log function
- Document how to bake a shaper + LUT combo
- Fix the various minor CSP LUT issues
- Ensure that the `colour.LUT_to_LUT` definition handles explicit domains
- Fix the `.spi3d` LUT indexing on read as per OCIO reference

#### Helpful Experience

- Knowledge of Numpy and Scipy
- Basic knowledge of Colour

#### First Steps

- Study the `colour.io.luts` sub-package
- Address one of the fixes or implement one of the minor features
