---
layout: page
title: "UG: Python Toolbox for Optimal Control"
description: Build a small, well-documented Python toolbox that solves classic optimal-control problems (brachistochrone, LQR, simple sweeping process) and visualizes trajectories.
img: assets/img/4.jpg
importance: 1
category: undergraduate
---

### Project at a glance

| | |
|---|---|
| **Level** | Undergraduate (AMS 487, or independent study) |
| **Prerequisites** | Calculus, basic ODEs, Python (NumPy / Matplotlib) |
| **Effort** | One semester (~4–6 hrs/week) |
| **Skills gained** | Numerical optimization, ODE solvers, scientific Python, technical writing |

### Goal

Implement and benchmark several classical optimal-control problems in Python, packaged as a small reusable toolbox with notebooks and figures.

### Suggested milestones

1. **Brachistochrone problem.** Discretize, solve with `scipy.optimize`, and reproduce the cycloid.
2. **Linear–quadratic regulator (LQR).** Implement the discrete-time Riccati recursion, compare with `python-control`.
3. **Simple sweeping process.** Implement the **catching-up algorithm** for a 1D / 2D test problem with a moving constraint set, and animate the trajectory.
4. **Write-up.** A short report (8–12 pages) and a Jupyter notebook demonstrating each example.

### Why it matters

It gives you a hands-on entry point into the **optimal-control + nonsmooth dynamics** world that drives a lot of modern research, and produces a portfolio artifact you can put on GitHub.
