---
layout: page
title: Paleomagnetism
description: Statistical modelling of paleomagnetic data and apparent polar wander paths
img: assets/img/paleomag-portrait.png
importance: 2
category: Geophysical Domains
related_publications: sapienza2025spherical, zhang2026enriching, GALLO2025119390, sapienza2026noise, sapienza2023quantitative, gallo2023embracing, gallo2022optimization, vasquez2018anhysteretic
---

Rocks record the direction of Earth's magnetic field at the time they formed.
Paleomagnetic data are therefore one of our main sources of information about the past motion of tectonic plates and the evolution of the geomagnetic field.
These data are scarce, noisy, unevenly distributed in time and supported on the sphere, which makes their statistical analysis challenging.

Together with collaborators in the [PolarWandering](https://github.com/PolarWandering) group, I work on data-driven methods for paleomagnetism, including
- **Apparent polar wander paths**: estimating smooth paths on the sphere with Universal Differential Equations ([SphereUDE.jl](https://github.com/ODINN-SciML/SphereUDE.jl)), and combining site-based paths with Bayesian age models.
- **Uncertainty quantification**: propagating uncertainty in paleomagnetic poles to plate reconstructions, as in our case study of Cenozoic North America.
- **Sampling strategies**: a quantitative analysis of how sampling design affects paleomagnetic estimates ([PaleoSampling](https://polarwandering.github.io/PaleoSampling/)).
- **Remagnetization**: identifying remagnetization sources with statistical learning.
- **Geomagnetic field dynamics**: using ordinal pattern statistics to ask whether the evolution of Earth's dipole is better explained by stochastic or chaotic dynamics.
