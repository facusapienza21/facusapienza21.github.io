---
layout: page
title: Physics & AI
description: Universal differential equations and statistics of physical time series
img: assets/img/conceptual-topics.jpg
importance: 2
category: Methods
related_publications: bolibar2023universal, sapienza2025spherical, sapienza2026noise
---

A large part of my work uses differential equations as regression mechanisms to model complex geophysical systems.
The physics we trust is encoded in the equations, while the parts that are poorly understood are learned from data.
This combines data-driven and physics-driven approaches in a single, interpretable model.

### Universal Differential Equations

Universal Differential Equations (UDEs) embed a regressor, such as a neural network or a set of basis functions, inside a differential equation.
Training the model means solving the differential equation and differentiating through its solution (see [Differentiable Programming](/projects/diffprog_project/)).
I use this framework for
- **Functional inversions**: learning empirical laws, such as the ice rheology in glacier flow models, directly from observations.
- **Regression on manifolds**: fitting smooth paths on the sphere from scarce and noisy data, with applications to paleomagnetism ([SphereUDE.jl](https://github.com/ODINN-SciML/SphereUDE.jl)).

### Ordinal patterns and statistics of physical time series

Geophysical signals are often poorly sampled and noisy, which makes it hard to tell what kind of dynamics produced them.
Ordinal pattern statistics, such as permutation entropy and the complexity-entropy plane, are a simple, model-free way to characterize the dynamics of a time series.
However, observational noise distorts these statistics and can lead to misclassifying a dynamical system.
Using majorization theory, I characterize these distortions and develop methods to correct them and to quantify measurement noise without fitting a model.
As an application, we use these tools to ask whether the evolution of Earth's magnetic dipole is better described by stochastic or chaotic dynamics.
Code is available in [NoisyCE.jl](https://github.com/facusapienza21/NoisyCE.jl).
