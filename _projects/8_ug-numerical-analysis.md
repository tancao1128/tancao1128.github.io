---
layout: page
title: "UG: Catching-Up Algorithm — Numerical Experiments"
description: Implement Moreau's catching-up algorithm in Python and experimentally verify the error bounds for several test problems.
img: assets/img/8.jpg
importance: 5
category: undergraduate
---

### Project at a glance

| | |
|---|---|
| **Level** | Undergraduate (AMS 326 / 487) |
| **Prerequisites** | Numerical analysis, Python, basic functional analysis helpful |
| **Effort** | Half to one semester |
| **Skills gained** | Numerical methods for nonsmooth ODEs, convergence-rate experiments, scientific reporting |

### Goal

Implement the **catching-up (algorithme de rattrapage)** time-discretization for several differential inclusions and **empirically measure the convergence rate**, comparing against theoretical $O(h)$ bounds.

### Suggested milestones

1. **Implement** the basic scheme: project the predicted state onto the moving admissible set at each step.
2. **Test problems.**
   - A 1D scalar inclusion with a known closed-form solution.
   - A 2D dry-friction system.
   - A planar sweeping process with a moving polygon.
3. **Experiments.** Plot error vs. step size on a log-log scale; estimate the empirical convergence order.
4. **Variable step sizes.** Try adaptive step-size strategies and measure efficiency.
5. **Write-up.** Short report with figures, comparing to the theoretical predictions in the *Applied Mathematics and Optimization* paper (Cao & Saoud, 2026).

### Why it matters

This is the **direct numerical companion** to an active research project. You'll see firsthand how rigorous error analysis translates into observable convergence behavior, and produce plots that could appear in a follow-up publication.
