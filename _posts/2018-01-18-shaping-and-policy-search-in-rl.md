---
layout: post
title: Shaping and policy search in reinforcement learning (ch.1&2)
tags: [paper, review, rl]
comments: true
mathjax: true
---

This paper is a dissertation of Andrew Ng. I have chosen to read this article because Professor Abbeel mentioned that chapter 1 and 2 from this article is great to know for MDP information.

- The "curse of dimensionality" is caused by discretized reinforcement problem. Then would action with continuous control is avoid the dimensional problem?
- 'Reward shaping' refers to the practice of choosing or modifying a reward function to help algorithms learn.
- The remarked thing about Partially Observable MDP (POMDP) is that it involves belief state tracking. Because the state is not fully observable, affected by other environment parameters, the general states are transformed to observation states and related to belief states. States are worked with distribution $$p(s)$$ over represented belief of what state we are in.
- In my opinion, according to this information, to handle POMDP environment is closely related to Bayesian methods. In general MDPs, all states are represented deterministically, and value or policy iteration methods are able to apply. Extending this, in POMDPs, state variables are represented with distribution and belief.

