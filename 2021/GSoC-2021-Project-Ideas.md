# GSoC 2021 - Project Ideas

## Colour Science for Python

[Colour](https://github.com/colour-science/colour) is an open-source [Python](https://www.python.org/) package providing a comprehensive number of
algorithms and datasets for colour science.

It is freely available under the [New BSD License](https://opensource.org/licenses/BSD-3-Clause) terms.

## Table of Contents <!-- omit in toc -->

- [GSoC 2021 - Project Ideas](#gsoc-2021---project-ideas)
  - [Colour Science for Python](#colour-science-for-python)
  - [Mentors](#mentors)
  - [Project Ideas](#project-ideas)
    - [*New Colour Models*](#new-colour-models)
      - [Abstract](#abstract)
      - [Technical Details](#technical-details)
      - [Helpful Experience](#helpful-experience)
      - [First Steps](#first-steps)
    - [*New Colour Appearance Models*](#new-colour-appearance-models)
      - [Abstract](#abstract-1)
      - [Technical Details](#technical-details-1)
      - [Helpful Experience](#helpful-experience-1)
      - [First Steps](#first-steps-1)

## Mentors

- [Michael Mauderer](https://github.com/MichaelMauderer)
- [Thomas Mansencal](https://github.com/KelSolaar)

## Project Ideas

### *New Colour Models*

#### Abstract

Colour implements many colour models such as CIE L\*a\*b\*, DIN99, CAM16-UCS
or JzAzBz. With the intent of being as thorough as possible, it is desirable
to add new colour models or extend existing ones.

| **Intensity** | **Priority** | **Involves**                                                             | **Mentors**                                                                                              |
|---------------|--------------|--------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|
| Moderate      | High         | Implementing new colour models and learning about colour transformations | [Michael Mauderer](https://github.com/MichaelMauderer), [Thomas Mansencal](https://github.com/KelSolaar) |

#### Technical Details

[Colour models](https://en.wikipedia.org/wiki/Color_model)
are at the core of colour representation, and are designed with different
objective in mind, e.g. user-friendly parameterization for image colour grading
for [HSV](https://en.wikipedia.org/wiki/HSL_and_HSV), perceptual uniformity for
[OSA-UCS](https://en.wikipedia.org/wiki/OSA-UCS), signal compression efficiency
for [ICtCp](https://en.wikipedia.org/wiki/ICtCp). The following colourspaces
would be good candidates for addition:

- [HCL](https://github.com/colour-science/colour/issues/564)
- [IHLS](https://github.com/colour-science/colour/issues/590)
- [ICaCb](https://github.com/colour-science/colour/issues/553)
- [ProLab](https://github.com/colour-science/colour/issues/675)
- [DIN99b, DIN99c, DIN99d](https://github.com/colour-science/colour/issues/771)
- [Y"u"v"](https://github.com/colour-science/colour/issues/659)
- [ULab](https://github.com/colour-science/colour/issues/770)

#### Helpful Experience

- Colour science knowledge
- Ability to read scientific publications
- Knowledge of Numpy and Scipy
- Basic knowledge of Colour

#### First Steps

- Study the `colour.models` sub-package
- Implement support for the HCL and IHLS colourspaces, possibly using existing contributions
- Implement support for the ICaCb colourspace, while at same time implementing a common
  base for the IPT-like spaces such as IPT, ICtCp, JzAzBz, and OKLab
- Implement support for the Prolab colourspace
- Implement support for the DIN99 variants while refactoring the common base
- Implement support for Y"u"v" colourspace and its chromaticity diagram plot
- Implement support for the ULab colourspace

### *New Colour Appearance Models*

#### Abstract

Colour implements various Colour Appearance Models (CAM), most notably Hunt,
CIECAM02 and CAM16. More models would be useful for research purposes,
especially for High Dynamic Range (HDR) image processing.

| **Intensity** | **Priority** | **Involves**                                                                      | **Mentors**                                                                                              |
|---------------|--------------|-----------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|
| Moderate      | High         | Implementing new colour appearance models and learning about advanced colorimetry | [Michael Mauderer](https://github.com/MichaelMauderer), [Thomas Mansencal](https://github.com/KelSolaar) |

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
- Replace the fixtures-based unit tests with regular unit tests consistent with the remaining of the codebase
- Implement Sadfar et al. (2018) CAM forward and reverse transformations
- Implement the remaining CAMs in the preferred following order:
    - Kim, Weyrich and Kautz (2009)
    - iCAM06
    - Comprehensive CAM
    - CAM15u