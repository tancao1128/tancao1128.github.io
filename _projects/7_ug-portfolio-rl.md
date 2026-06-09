---
layout: page
title: "UG: Policy Gradient for Mean-Variance Portfolio Optimization"
description: Reproduce a regime-switching financial market and train a policy-gradient agent to balance expected return and variance — a bridge between optimization, finance, and RL.
img: assets/img/7.jpg
importance: 4
category: undergraduate
---

### Project at a glance

| | |
|---|---|
| **Level** | Undergraduate research (AMS 487 / 341) |
| **Required courses** | [AMS 261 — Applied Calculus III](https://www.stonybrook.edu/ams/academics/undergraduate/ug-courses/ams-261.html) and [AMS 210 — Applied Linear Algebra](https://www.stonybrook.edu/ams/academics/undergraduate/ug-courses/ams-210.html) |
| **Optional** | [AMS 361 — Applied Calculus IV: Differential Equations](https://www.stonybrook.edu/ams/academics/undergraduate/ug-courses/ams-361.html) |
| **Preferred** | [AMS 326 — Numerical Analysis](https://www.stonybrook.edu/ams/academics/undergraduate/ug-courses/ams-326.html) |
| **Programming** | Python (NumPy required; PyTorch helpful, can be learned during the project) |
| **Effort** | One semester (≈ 6–9 hrs/week) |
| **Skills gained** | Policy-gradient RL, stochastic optimization, PyTorch, quantitative finance modeling |

### What you will actually do

Over one semester you will build, from scratch, a small but complete research pipeline:

- **Simulate a financial market** whose statistical behavior switches between hidden *regimes* (e.g. bull / bear / sideways), modeled as a Markov chain.
- **Derive and code the classical mean-variance benchmark** — the Markowitz-style optimal allocation when the regime is known — to serve as a yardstick.
- **Train a reinforcement-learning agent** (REINFORCE, then actor–critic) that learns a portfolio-allocation *policy* directly from simulated price paths, optimizing a reward that rewards return and penalizes variance.
- **Run experiments and write up results** — compare the learned policy against the benchmark on Sharpe ratio, drawdown, and per-regime behavior, and present the findings in a short report and a group talk.

By the end you will have a working RL system, a set of reproducible plots, and a written report suitable for an honors thesis, a research-experience application, or a quant-finance internship portfolio.

### Goal

Implement a **regime-switching market** (Markov chain over bull/bear/sideways regimes) and train a **REINFORCE / actor–critic** agent to learn a portfolio policy that trades off mean return against variance.

### Suggested milestones

1. **Market simulator.** Implement a 3-regime Markov-switching model with regime-dependent asset returns.
2. **Baseline.** Compute the classical mean-variance optimal portfolio under a known regime.
3. **RL agent.** Train a policy-gradient agent on the simulated market with a mean-variance reward.
4. **Comparison.** Plot Sharpe ratio, max drawdown, and learned regime-specific allocations.
5. **(Bonus)** Compare against an LSTM-augmented policy that uses recent returns as input.

### Why these courses?

| Course | Why it is needed |
|---|---|
| **AMS 261 (required)** | Multivariable calculus — gradients and the chain rule underlie every policy-gradient update. |
| **AMS 210 (required)** | Linear algebra — covariance matrices, the mean-variance objective, and PyTorch tensors are all linear-algebraic. |
| **AMS 361 (optional)** | Differential equations — helps in understanding continuous-time market dynamics and the bonus continuous-model extension. |
| **AMS 326 (preferred)** | Numerical analysis — gives you the stability, convergence, and floating-point intuition that makes the training loop trustworthy rather than a black box. |

If you have taken AMS 261 and AMS 210 and are comfortable writing Python, you are ready to apply; AMS 326 simply lets you go deeper, faster.

### Why it matters

This is the undergraduate-friendly version of an ongoing research project (with L. Vu) on **policy-gradient methods for mean-variance portfolio optimization under regime-switching dynamics**. You will gain transferable skills for both academic ML research and quantitative finance roles.

### How to apply

Email me (see the [contact page](/)) with: (1) the AMS courses you have completed and your grades in AMS 261 and AMS 210, (2) a one-paragraph note on why this project interests you, and (3) any prior Python or finance experience. No published research is expected — curiosity and follow-through matter most.
