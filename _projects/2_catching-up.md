---
layout: page
title: Catching-Up Algorithm for Differential Inclusions
description: Convergence, stability, and quantitative error bounds for discretizations of differential inclusions driven by maximal monotone operators.
img: assets/img/2.jpg
importance: 2
category: research
related_publications: true
---

The **catching-up algorithm** (Moreau's *algorithme de rattrapage*) is a time-discretization scheme that constructs piecewise-constant approximate solutions of differential inclusions by projecting onto admissible sets at each step. It is the foundational numerical tool for sweeping processes and projected dynamical systems.

### Current work (with Hassan Saoud, Gulf University)

We study a catching-up scheme for differential inclusions driven by **maximal monotone operators with continuous perturbations**, decomposing the operator into its single-valued part and the normal cone to a closed convex set. The work establishes:

- Existence and global energy bounds under a mild **tangent dissipativity** assumption.
- Uniqueness and stability with respect to initial data under local Lipschitz perturbations.
- **Quantitative error bounds** and uniform boundedness of iterates for the variable-step-size scheme with approximate projections.
- Asymptotic feasibility of the predictor step in an $L^2$ sense and a Cesàro-averaged feasibility property.
- Explicit examples: a one-dimensional test case and a multidimensional dry-friction system.

📄 **Status:** submitted to *Applied Mathematics and Optimization* (2026).

### Related research

- Catching-up with errors for sweeping processes driven by a fixed set.
- Connections to projected dynamical systems and complementarity problems.
