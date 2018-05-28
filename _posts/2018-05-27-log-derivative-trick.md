---
layout: post
title : Log Derivative Trick
---

- Alternating between normalized-probabilities and log-probabilities
- The derivative of the logarithm trick well-used to solve stochastic optimization problems.

## Score Functions

- The central computation for MLE, often used in generalized linear regression, deep learning, kernel machines, dimensionality reduction, and tensor decompositions
- The expected value of the score is zero. (used in the proof of REINFORCE algorithm)
- The variance of the score is the Fisher information. It is used to determine the Cramer-Rao lower bounds.


  $$\mathbb{V}$$$$[\nabla_\theta log\; p(\textbf{x};\theta)]$$ = $$\mathbb{I}(\theta)$$ = $$\mathbb{E}_{p(x;\theta)}$$$$[\nabla_\theta log\; p(\textbf{x};\theta)\nabla_\theta log\; p(\textbf{x};\theta)^T]$$

## Score Function Estimators


  $$\nabla_\theta\mathbb{E}_{p(z;\theta)}$$$$[f(z)] = \nabla_\theta$$$$\int$$$$p(z;\theta)f(z)dz$$


- A recurring task in ML
  - Posterior computation in VI
  - Value function and policy learning in RL
  - Derivative pricing in computational finance
  - Inventory control in operations research
- The gradient of expectation of function $$f$$ is difficult to compute, because the integral is typically unknown and the parameters $$\theta$$, with respect to which we are computing the gradient, are of the distribution $$p(z;\theta)$$.
- Moreover, we (perhaps) want to compute this gradient when the function $$f$$ is not differentiable.
- Score function is an unbuased estimator of the gradient.
  - The function $$f(z)$$ need not be differentiable. Instead, we should be able to evaluate it or observe its value for a given $$z$$.


  $$\nabla_\theta\mathbb{E}_{p(z;\theta)}[f(z)] =$$ $$\mathbb{E}_{p(z;\theta)}[f(z)\nabla_\theta log\; p(z;\theta)]$$


1. Score function estimators
2. Likelihood ratio methods
3. Automated variational inference
4. REINFORCE and policy gradients
  1. Any gradients of the policy that correspond to high rewards are weighted higher—reinforced—by the estimator.
  2. The estimator was called REINFORCE, and its generalization now forms the policy gradient theorem.

## Control Variates

- To make MC estimator effective, its variance is as low as possible. 
  (The gradient will not be useful otherwise.)
- Control variates: used for variance reduction in MC estimators (baseline technique)


  $$\nabla_\theta\mathbb{E}_{p(z;\theta)}[f(z)] = \mathbb{E}_{p(z;\theta)}[(f(z)-\lambda)\nabla_\theta log\; p(z;\theta)]$$


- The choice of control variate is the principal challenge in the use of the score function estimators.
- Ex. Constant baselines, clever sampling schemes (antithetic or stratified), delta methods, or adaptive baselines

## Familes of Stochastic Estimators

$$PD:\qquad \nabla_\theta\mathbb{E}_{p(z;\theta)}[f(z)] =$$ $$\mathbb{E}_{p(\epsilon)}[\nabla_\theta f(g(\epsilon,\theta))]$$
$$SF:\qquad\nabla_\theta\mathbb{E}_{p(z;\theta)}[f(z)] = \mathbb{E}_{p(z;\theta)}[f(z)\nabla_\theta log\;p(z;\theta)]$$


- Approaches
  - Differentiate the function f, using pathwise derivatives, if it is differentiable
  - Differentiate the density $$p(z)$$, using the score function
- Using stochastic computation graph, PD and SF can be combined (providing the lowest variance)

