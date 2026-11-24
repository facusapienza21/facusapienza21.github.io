---
layout: page
title: Differentiable Programming
description: Gradients through numerical solvers of differential equations
img: assets/img/diffprog-portrait.png
importance: 1
category: Methods
related_publications: sapienza2024differentiable, bolibar2023universal
---

Many problems in the geosciences require computing gradients of a loss function with respect to the parameters of a model governed by differential equations.
Differentiable programming makes it possible to compute these gradients efficiently and accurately, so that numerical solvers can be combined with optimization and machine learning.

I am interested in the mathematical, computational and practical aspects of these sensitivity methods, including
- Forward and reverse mode automatic differentiation
- Continuous and discrete adjoint methods
- Trade-offs between accuracy, memory and computational cost, and the stability of the gradients
- Implementation in the Julia SciML ecosystem

Together with collaborators, we wrote a [review paper](https://github.com/ODINN-SciML/DiffEqSensitivity-Review) on sensitivity methods for differential equations, aimed at domain scientists who want to bring these tools into their research.
These methods are the computational backbone of [ODINN](/projects/odinn_project/) and [SphereUDE.jl](https://github.com/ODINN-SciML/SphereUDE.jl).
