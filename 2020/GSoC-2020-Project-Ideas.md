# GSoC 2020 - Project Ideas

## Colour Science for Python

[Colour](https://github.com/colour-science/colour) is an open-source [Python](https://www.python.org/) package providing a comprehensive number of
algorithms and datasets for colour science.

It is freely available under the [New BSD License](https://opensource.org/licenses/BSD-3-Clause) terms.

## Mentors

- [Michael Mauderer](https://github.com/MichaelMauderer)
- [Thomas Mansencal](https://github.com/KelSolaar)

## Project Ideas

### *The Need for Speed*

#### Abstract

Most of Colour's code is vectorised, leverages [Numpy]([NumPy — NumPy](https://numpy.org/), while trying to be as faithful as possible to the scientific publications implemented. Speed has never been the primary focus for the development, however, it is often an important factor to consider when adopting a library thus we would like to improve the general performance of Colour.

| **Objectives** | **Difficulty** | **Mentors** |
| --- | --- | --- |
| Implementing a benchmarking suite, measuring performance, improving speed in image processing hotspots, and investigating usage of [CuPy](https://cupy.chainer.org/), [Bohrium](https://github.com/bh107/bohrium) or any relevant GPU backend. | Medium | [Michael Mauderer](https://github.com/MichaelMauderer), [Thomas Mansencal](https://github.com/KelSolaar) |

#### Detailed Description

Performance measurements requires the creation of a benchmarking suite. [Airspeed Velocity (ASV)](https://asv.readthedocs.io/) is a tool for benchmarking Python packages, used by [scikit-image](https://scikit-image.org/docs/dev/contribute.html#benchmarks). It might be helpful to manage the benchmarking suite. Good performance is expected when processing large images, e.g HD1080, UHD resolution, thus focusing on image processing transformations such as CIE XYZ to CIE Lab is preferred. CuPy and Bohrium are two GPU backends of interest: they offer an almost standin Numpy like API. They might provide significant performance improvement for a minimal amount of work.

#### Initial Steps

- Investigate ASV
- Design the foundations of a benchmarking suite for Colour
- Discuss with the Colour developers about the preferred transformations to measure the performance of and benchmark them
- Investigate possible optimizations and GPU backends

#### Useful Experience

- Experience with testing or benchmarking numerical code
- Knowledge of Numpy, Scipy, vectorisation and GPU programming
- Basic knowledge of Colour

### *New Colour Appearance Models*

#### Abstract

Colour implements various Colour Appearance Models (CAM), most notably Hunt, CIECAM02 and CAM16. Various new models would be useful for research purposes, especially for High Dynamic Range (HDR) imagery processing.

| **Objectives** | **Difficulty** | **Mentors** |
| --- | --- | --- |
| Implement new Colour Appearance Models. | Medium | [Michael Mauderer](https://github.com/MichaelMauderer), [Thomas Mansencal](https://github.com/KelSolaar) |

#### Detailed Description

[Colour appearance modeling](https://en.wikipedia.org/wiki/Color_appearance_model) is critical to the prediction of colours under different viewing conditions. The current model recommended by the [CIE](http://cie.co.at/) is [CIECAM02](https://en.wikipedia.org/wiki/CIECAM02) and is not designed to process HDR imagery. [Sadfar et al. (2018)](https://doi.org/10.2352/ISSN.2169-2629.2018.26.96) proposed a new CAM based on JzAzBz colourspace with support for HDR imagery. Other CAMs such as [iCAM06](https://doi.org/10.1016/j.jvcir.2007.06.003), [Kim, Weyrich and Kautz (2009)](https://dl.acm.org/doi/abs/10.1145/1531326.1531333), the [Comprehensive CAM](https://doi.org/10.1002/col.22078), and [CAM15u](https://doi.org/10.1364/OE.23.012045) are also prime candidates for inclusion.

#### Initial Steps

- Study the `colour.appearance` sub-package
- Implement Sadfar et al. (2018) CAM forward and reverse transformations
- Implement the remaining CAMs in the preferred following order:
    - iCAM06
    - Kim, Weyrich and Kautz (2009)
    - Comprehensive CAM
    - CAM15u

#### Useful Experience

- Colour sicence and colour appearance modeling
- Knowledge of Numpy and Scipy
- Basic knowledge of Colour

### *New Colour Quality Metrics*

#### Abstract

The CIE current recommended method for measuring Colour Quality is the [CIE 2017 Colour Fidelity Index (CFI 2017)](http://cie.co.at/publications/cie-2017-colour-fidelity-index-accurate-scientific-use). It supersedes the [Colour Rendering Index (CRI)](https://en.wikipedia.org/wiki/Color_rendering_index) and should be implemented in Colour along with the related [IES TM-30-15](http://www.ies.org/store/product/ies-method-for-evaluating-light-source-color-rendition-3368.cfm).

| **Objectives** | **Difficulty** | **Mentors** |
| --- | --- | --- |
| Implement new Colour Quality Metrics. | Medium | [Michael Mauderer](https://github.com/MichaelMauderer), [Thomas Mansencal](https://github.com/KelSolaar) |

#### Detailed Description

Colour implements the SSI, CRI and CQS quality metrics, the two latter have been superseded with IES TM-30-15 and CFI 2017. To bring Colour up to latest standards, those two metrics need to be implemented.

#### Initial Steps

- Study the `colour.quality` sub-package
- Implement IES TM-30-15
- Implement CFI 2017

#### Useful Experience

- Colour sicence and colour quality
- Knowledge of Numpy and Scipy
- Basic knowledge of Colour

### *LUT IO Improvements*

#### Abstract

| **Objectives** | **Difficulty** | **Mentors** |
| --- | --- | --- |

#### Detailed Description

#### Initial Steps

#### Useful Experience

- Knowledge of Numpy and Scipy
- Basic knowledge of Colour