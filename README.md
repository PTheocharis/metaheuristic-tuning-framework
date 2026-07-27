# AutoML Meets Metaheuristics
### Hyperparameter Optimization of a Scheduling Problem via Surrogate-Assisted Search

Bachelor Thesis – Department of Management Science & Technology  
Athens University of Economics and Business

---

## Overview

This thesis investigates whether **Automated Machine Learning (AutoML)** techniques can effectively replace manual hyperparameter tuning in **metaheuristic optimization**.

The study applies Bayesian Hyperparameter Optimization methods to tune a **Genetic Algorithm (GA)** solving an **Unrelated Parallel Machine Scheduling (UPMS)** problem with **sequence-dependent setup times**, aiming to minimize **total weighted tardiness**.

Instead of relying on manually selected parameter combinations, the Genetic Algorithm is treated as a **black-box optimization problem**, allowing AutoML frameworks to search for improved configurations automatically.

---
## Key Research Idea
Traditional optimization research often focuses on improving the optimization algorithm itself

This work explores another direction:
-Instead of manually designing the best algorithm configuration, allow automated optimization methods to discover effective configurations.

This connects Operations Research with modern approaches from;
-Automated Machine Learning
-Bayesian Optimization
-Algorithm Configuration
-Intelligent Decision Support
---
## Research Objectives

The main objectives of this work were to:

- evaluate the applicability of AutoML to metaheuristic tuning
- benchmark modern Bayesian Optimization methods against expert manual tuning
- analyze solution quality, robustness and computational efficiency
- investigate whether AutoML can improve optimization under increasingly difficult scheduling instances
- provide a reusable and extensible tuning framework for future research

---

## Methodology

The experimental pipeline consists of:

- Adapted Genetic Algorithm (based on Avgerinos et al.)
- AutoML wrapper treating the GA as a black-box objective
- Hyperparameter Optimization using Optuna
- Repeated stochastic evaluations for robust comparison
- Benchmarking on synthetic scheduling instances of increasing complexity

### Scheduling Problem

- Unrelated Parallel Machine Scheduling (UPMS)
- Sequence-dependent setup times
- Weighted Tardiness minimization

### Optimized Hyperparameters

- Population size
- Number of generations
- Crossover rate
- Mutation rate

---

## Hyperparameter Optimization Methods

Three tuning strategies were compared:

| Method | Description |
|----------|-------------|
| Grid Search | Expert-designed manual baseline |
| GP + Expected Improvement | Gaussian Process Bayesian Optimization |
| Tree-structured Parzen Estimator (TPE) | Density-based Bayesian Optimization |

Implementation was developed using **Optuna**, with custom stopping criteria and repeated evaluations to reduce stochastic noise.

---

## Experimental Setup

The benchmark consists of **24 scheduling instances** divided into four problem sizes:

- 25 × 5
- 50 × 5
- 50 × 10
- 100 × 10

Each configuration was evaluated through multiple independent GA executions to improve result reliability.

Performance was assessed using:

- Total Weighted Tardiness
- Relative Improvement (%)
- Standard Deviation
- Runtime
- Number of evaluated configurations
- Search efficiency

---

# Results

The experimental evaluation demonstrates that **AutoML is a viable alternative to manual hyperparameter tuning for metaheuristics.**

### Main findings

- GP + Expected Improvement consistently produced the strongest overall performance.
- AutoML outperformed manually tuned Grid Search in the majority of tested instances.
- Improvements became increasingly significant as scheduling complexity increased.
- Smaller scheduling instances exhibited only marginal gains, indicating diminishing returns where manual tuning is already near-optimal.
- GP+EI showed better stability and lower variability than TPE in most experiments.
- TPE remained competitive while displaying higher sensitivity to instance characteristics.
- AutoML achieved better solutions while requiring less manual effort and providing a reproducible optimization workflow.

One of the most notable observations is that **the benefits of Bayesian Optimization grow together with problem complexity**, suggesting that AutoML becomes increasingly valuable for computationally demanding scheduling problems.

---

## Technologies

- Python
- Optuna
- Bayesian Optimization
- Gaussian Processes
- Tree-structured Parzen Estimator (TPE)

---

## Repository Structure

```
.
├── Thesis.pdf
└── README.md
```

---

## Thesis

The complete thesis is available in:

```
Thesis.pdf
```

---

## Citation

If you use this work for academic purposes, please cite:

> Theocharis, P. (2025). *AutoML Meets Metaheuristics: Hyperparameter Optimization of a Scheduling Problem via Surrogate-Assisted Search*. Bachelor Thesis, Athens University of Economics and Business.

---

## Future Work

Potential extensions include:

- larger benchmark datasets
- additional metaheuristics (ACO, PSO, Simulated Annealing, Tabu Search)
- multi-objective optimization
- advanced Bayesian Optimization frameworks (BoTorch)
- transfer learning between scheduling instances
- distributed and parallel optimization