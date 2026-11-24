---
layout: page
title: Fermat Distance
description: Density-based distances for manifold learning and clustering
img: assets/img/fermat-portrait.png
importance: 2
category: Past Projects
related_publications: sapienza2018weighted, groisman2022nonhomogeneous, chazal2023choosing, math-thesis
---

Many machine learning methods depend on a notion of distance between data points.
The Fermat distance is a sample-based distance inspired by Fermat's principle in optics: paths are shorter through regions of high data density.
It adapts to both the geometry of the data and its underlying density, which improves clustering and manifold learning.

We studied its theoretical properties through the lens of nonhomogeneous Euclidean first-passage percolation, how to choose its parameter in the presence of noise, and its use in practice.
Code is available in the [fermat](https://github.com/Fermat-distance/fermat) Python library.
