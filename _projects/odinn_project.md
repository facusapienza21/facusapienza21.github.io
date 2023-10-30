---
layout: page
title: ODINN
description: Glacier modelling using neural differential equations in Julia
img: assets/img/odinn-portrait.png
importance: 1
category: Machine Learning and Geophysics
related_publications: bolibar2023universal
---

Mountain glaciers, sea ice and ice sheets are the canary in the coal mine of climate change. 
They play a critical role on the delicate balance of our planet.
Understanding the governing laws of ice masses is critical from both scientific and social perspectives. 
Furthermore, with the advent of new remote sensing datasets with global coverage (~220.000 mountain glaciers), there is a need for desinging models based on geophysical principles but that can learn from observations. 
<!-- The glaciology community has historically been split between the glacier modelling and the remote sensing observational traditions.  -->
<!-- Fundamental improvements are needed in both areas, and critically, better merging of both approaches.  -->

Machine learning offers a new posibility to learn more complex and empirically accurate laws that underlie ice flow. 
Automated learning approaches are particularly suited to integrate the vast flood of new remote sensing data, creating feedback between models and data that accurately captures the underlying uncertainties in an interpretable manner. 
This problem requires statistics, physics, numerical modeling and data engineering infrastructure.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/malchin.jpg" title="Malchin Peak" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Picture taken from the Malchin Peak in Mongolia in the Altai Mountains, right in the border between Mongolia, Russia and China. 
</div>

In collaboration with [Jordi Bolibar](https://jordibolibar.wordpress.com/), [Fernando Pérez](https://bids.berkeley.edu/people/fernando-perez), among others, we work in the development of `ODINN.jl`, an open-source glacier evolution model in the Julia programming language,
Glacier dynamics can be modelled with differential equations, although classical approaches are not suitable for assimilating large spatio-temporal datasets, and they are becoming increasingly harder to optimize. 
ODINN is based in Universal Differential Equations, a novel approach where learning task can be incorporated inside numerical solvers for differential equations.
Parts of the equation (e.g. a parameter) can be learnt by a regressor (e.g. a neural network or a set of basis functions), which provides the model with more flexibility. 
This model is built on top of the Open Global Glacier Model (OGGM) in Python, one of the most popular frameworks for large-scale glacier modelling. 
Our final goal is to calibrate and validate this glacier evolution model with remote sensing data and climate reanalyses in order to understand past glacier changes and the role played by ice dynamics and mass balance.

{% raw %}
```math
\frac{\partial H}{\partial t} = \dot b + \nabla \cdot (D \nabla S)
```
{% endraw %}

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/ODINN_overview.jpg" title="ODINN Diagram" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Diagram of the workflow in ODINN. 
</div>

Some of the features of ODINN are 
- Efficient implementetion of the 2D SIA equation for mountain glaciers
- Implemented differential programming toold in the Julia SciML ecosystem that allows to compute gradients in the numerical solver for the 2D SIA equation
- Python-Julia integration via `PyCall.jl` that allow us to run libraries like `Xarray` and `OGGM` inside ODINN

Some ongoing work in progress
- Writing of [review paper]() about sensitivity methods for differential equations, that is, the differential programming capabilities that enable all the workflow inside ODINN. 

<!-- {% raw %}
```julia
using ODINN

1 + 1
```
{% endraw %} -->
