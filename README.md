# Data-Driven Chance-Constrained Multiple-Choice Knapsack Problem (CCMCKP)

## Overview
This repository contains the research and implementation for solving the **Chance-Constrained Multiple-Choice Knapsack Problem (CCMCKP)**. This is a classic NP-hard combinatorial optimization problem where item weights are modeled as random variables rather than fixed values.

The project proposes a data-driven framework that transforms stochastic chance constraints into deterministic risk-averse constraints using the Central Limit Theorem (CLT). It introduces three solution methods tailored for different problem scales, with a focus on scalability and solution quality in large-scale scenarios.

## Key Contributions
*   **Data-Driven Constraint Transformation:** Leverages CLT to infer normal distributions from historical data, converting probabilistic constraints into deterministic risk-averse formulations without relying on slow Monte Carlo simulations.
*   **RADP (Risk-Aware Dynamic Programming):** An exact algorithm based on dynamic programming that guarantees global optimality for small-scale instances.
*   **RAGA (Risk-Aware Genetic Algorithm):** A hybrid approximate method combining genetic algorithms with iterative RAMCKP solving. RAGA significantly outperforms standard GAs in both solution quality and computational efficiency for medium-to-large scale problems.
*   **Iterative Linearization Framework:** Transforms the nonlinear CCMCKP into a series of linear Risk-Aware MCKP (RAMCKP) subproblems, enabling efficient exploration of the feasible region via slope refinement in the Variance-Mean plane.

## Problem Formulation
The CCMCKP minimizes total cost subject to a chance constraint:

$$
\min \sum_{i=1}^{m} \sum_{j \in N_i} c_{ij} x_{ij}
$$

$$
\text{s.t. } \quad P\left(\sum_{i=1}^{m} \sum_{j \in N_i} w_{ij} x_{ij} \leq W\right) \geq P_0
$$

where $w_{ij} \sim \mathcal{N}(\mu_{ij}, \sigma_{ij}^2)$ are normally distributed weights inferred from data, and $P_0$ is the confidence threshold (default: 0.99).
