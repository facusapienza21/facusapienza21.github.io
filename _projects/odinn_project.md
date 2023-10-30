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
Understanding and predicting the future behaviour of ice on Earth is critical from both scientific and social perspectives. 
I am mostly motivated by understanding the effect that global warming has on the ice on Earth. 

The glaciology community has historically been split between the glacier modelling and the remote sensing observational traditions. 
Fundamental improvements are needed in both areas, and critically, better merging of both approaches. 
Automated learning approaches are particularly suited to integrate the vast flood of new remote sensing data, creating feedback between models and data that accurately captures the underlying uncertainties in an interpretable manner. 
This problem requires statistics, physics, numerical modeling and data engineering infrastructure in a highly interdisciplinary team. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/malchin.jpg" title="Malchin Peak" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Picture taken from the Malchin Peak in Mongolia in the Altai Mountains, right in the border between Mongolia, Russia and China. 
</div>

In collaboration with [Jordi Bolibar](https://jordibolibar.wordpress.com/), [Fernando Pérez](https://bids.berkeley.edu/people/fernando-perez), among others, in the development of `ODINN.jl`, an open-source glacier evolution model in the Julia programming language, based on Universal Differential Equations. 
Glacier dynamics can be modelled with differential equations, although classical approaches are not suitable for assimilating large spatio-temporal datasets, and they are becoming increasingly harder to optimize. 
However, sub-parts of the equation (e.g. a parameter) can be learnt by a regressor (e.g. a neural network or a set of basis functions), which provides the model with more flexibility. 
This model is built on top of the Open Global Glacier Model (OGGM) in Python, one of the most popular frameworks for large-scale glacier modelling. 
Our final goal is to calibrate and validate this glacier evolution model with remote sensing data and climate reanalyses in order to understand past glacier changes and the role played by ice dynamics and mass balance.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/ODINN_overview.pdf" title="ODINN Diagram" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Diagram of the workflow in ODINN. 
</div>



{% raw %}
```julia
using ODINN

1 + 1
```
{% endraw %}
