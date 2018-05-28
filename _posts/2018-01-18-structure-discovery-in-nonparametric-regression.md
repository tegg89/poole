---
layout: post
title: Structure discovery in nonparametric regression through compositional kernel search
---

This paper is related to Gaussian processes, especially in searching kernels. The core idea is that complicated kernels can be composited with commonly used kernel families, the squared exponential, periodic, linear, and rational quadratic.

- Kernels used in Gaussian processes are positive semidefinite ($x^TAx > 0$) which means they are closed under addition and multiplication operators.
- Kernels are the most important feature in Gaussian processes, specifying which structures are likely under the GP prior, which in turn determines the generalization properties of the model.
- Example expressions of composition kernels are shown below.
![example expressions](https://github.com/tegg89/tegg89.github.io/blob/master/images/2018-01-18-examples.png?raw=true)

- Generally, nonparametric regression gets drawback in posing high-dimensions, causing computation inefficiency. It says that learning 10 one-dimensional kernels is much easier than learning 1 ten-dimensional kernel. Whenever treating high-dimensional data, try to decompose complicate kernel into easier ones.
- According to experiments with time series data, more base kernels are composited, better regression resultant comes. Here, the 'depth' is used to matter how many base kernels are used. More depths, the kernel can capture the most of the relevant structure.
- Comparing to other methods: linear regression, Generalized Additive Models (GAM), GP with a standard SE kernel using Automatic Relevance Determination (GP SE-ARD), additive GPs, and kernel-search method of Hierarchical Kernel Learning (HKL); structure search outperforms of all in high-dimensional prediction task.

