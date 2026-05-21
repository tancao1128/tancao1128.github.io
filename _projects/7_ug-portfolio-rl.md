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
| **Level** | Undergraduate (AMS 487 / 341) |
| **Prerequisites** | Probability, basic finance helpful, Python (NumPy / PyTorch) |
| **Effort** | One semester |
| **Skills gained** | Policy-gradient RL, stochastic optimization, PyTorch, finance applications |

### Goal

Implement a **regime-switching market** (Markov chain over bull/bear/sideways regimes) and train a **REINFORCE / actor–critic** agent to learn a portfolio policy that trades off mean return against variance.

### Suggested milestones

1. **Market simulator.** Implement a 3-regime Markov-switching model with regime-dependent asset returns.
2. **Baseline.** Compute the classical mean-variance optimal portfolio under a known regime.
3. **RL agent.** Train a policy-gradient agent on the simulated market with a mean-variance reward.
4. **Comparison.** Plot Sharpe ratio, max drawdown, and learned regime-specific allocations.
5. **(Bonus)** Compare against an LSTM-augmented policy that uses recent returns as input.

### Why it matters

This is the undergraduate-friendly version of an ongoing research project (with L. Vu) on **policy-gradient methods for mean-variance portfolio optimization under regime-switching dynamics**. You will gain transferable skills for both academic ML research and quantitative finance roles.
