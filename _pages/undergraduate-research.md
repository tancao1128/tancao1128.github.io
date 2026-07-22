---
layout: page
title: undergraduate research preparation
permalink: /undergraduate-research/
description: A course and skills roadmap for students preparing to work with Prof. Tan Cao in optimal control, nonsmooth dynamics, robotics, traffic and crowd models, or safe reinforcement learning.
nav: false
toc:
  sidebar: left
---

Students interested in research with me should build more than a list of completed
courses. The goal is to become able to **formulate a model, implement and verify a
method, run an independent experiment, and explain the result clearly**.

This roadmap is mentoring guidance rather than a substitute for official degree
advising. Course offerings and prerequisites may change, so students should check
the current catalog and consult the AMS undergraduate advisor.

## Core roadmap

| Stage                               | Recommended preparation                                                      | What it enables                                                                                    |
| ----------------------------------- | ---------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| **1. Mathematical foundation**      | AMS 151–161, AMS 261, AMS 210                                                | Calculus, multivariable modeling, vectors, matrices, eigenvalues, and projections                  |
| **2. Dynamics and computation**     | AMS 361 or MAT 303; CSE 101/114 or AMS 325; AMS 326                          | ODE models, scientific programming, numerical solvers, and convergence checks                      |
| **3. Optimization and uncertainty** | AMS 341; AMS 310 followed by AMS 311; AMS 342 when relevant                  | Deterministic optimization, duality, probability, and stochastic modeling                          |
| **4. Track electives**              | AMS 345, AMS 380, AMS 394, AMS 412, MAT 331, or proof-oriented MAT courses   | Robotics geometry, machine learning, experimental analysis, research computing, and proof maturity |
| **5. Research bridge**              | A 4–6 week trial project, followed by AMS 487 if the decision gate is passed | Independent experimentation, reproducibility, technical writing, and research fit                  |

## The hard core

These subjects form the common foundation for most projects in my group:

- **AMS 210 — Applied Linear Algebra:** linear systems, eigenvalues, inner
  products, and projections.
- **AMS 261 — Applied Calculus III:** multivariable derivatives, gradients, and
  constrained modeling.
- **AMS 361 or MAT 303 — Differential Equations:** continuous-time dynamics and
  systems of ODEs.
- **Scientific programming:** an approved programming course such as CSE 101,
  CSE 114, or AMS 325, followed by practical use of Python, NumPy, SciPy,
  Matplotlib, and Jupyter.
- **AMS 326 — Numerical Analysis:** discretization, numerical error, stability,
  and verification.

For students seeking deeper theoretical work or graduate study, I also recommend
**MAT 200** (language, logic, and proof), **MAT 319 or MAT 320** (analysis), and
**MAT 310** (advanced linear algebra), subject to prerequisites and availability.

## Choose a research direction

### Optimal control and sweeping processes

Recommended sequence:

**AMS 210 → AMS 261 → AMS 361/MAT 303 → AMS 326 → AMS 341.**

This path develops the linear algebra, ODEs, numerical methods, and deterministic
optimization needed for controlled dynamical systems. Students interested in
theorem-oriented work should add MAT 200, MAT 319/320, and MAT 310.

### Robotics and navigation

Start with the common core, then prioritize **AMS 301, AMS 341, and AMS 345**.
AMS 345 is especially relevant because it includes computational geometry,
visibility, geometric algorithms, and robot motion planning. MAT 331 can provide
additional project-oriented computing experience when available.

### Safe reinforcement learning and learning-based control

Start with the common core, then take **AMS 310 → AMS 311**, followed by
**AMS 342 or AMS 380**. AMS 380 adds statistical learning and Python
implementation, while AMS 394 is useful for experimental design, data analysis,
and reporting. Students should learn probability and numerical verification
before treating reinforcement learning as more than a software exercise.

### Traffic flow, crowd motion, and dynamical modeling

Prioritize **AMS 361/MAT 303, AMS 326, and AMS 341**. Add MAT 341 when partial
differential equations become central. Students should first master ODE
simulation, conservation checks, and numerical error analysis before moving to
PDE discretizations or interacting-agent models.

## From coursework to AMS 487

Coursework is preparation, not evidence of research readiness. A typical path is:

1. Complete the mathematical and computational foundation.
2. Select one research direction rather than trying to prepare for every topic.
3. Reproduce a known benchmark with tested code and a short explanation.
4. Complete a structured 4–6 week trial project.
5. Proceed to AMS 487 only after demonstrating correctness, independence,
   verification, and clear writing.

### Trial-project readiness gate

Before beginning AMS 487, a student should be able to:

- implement Euler and RK4 and verify the observed convergence order;
- organize code in a reproducible notebook or repository;
- explain the model and all variables in their own words;
- derive or justify at least one central formula used in the implementation;
- design and interpret a numerical experiment independently;
- write a concise 2–5 page technical report; and
- state clearly what the experiment does **not** establish.

> **Mentoring policy.** Strong grades are helpful but not sufficient. AMS 487
> follows a successful trial project; it is not the place to begin learning basic
> programming, ODE solvers, or mathematical writing.

## Explore possible projects

The [undergraduate project descriptions](/projects/#undergraduate) show how this
preparation leads to concrete work in optimal control, sweeping processes,
navigation, reinforcement learning, and numerical analysis.

## Official course information

- [SUNY Korea AMS major requirements](https://ams.sunykorea.ac.kr/ams/html/sub03/030801.html)
- [SUNY Korea AMS course syllabi](https://ams.sunykorea.ac.kr/ams/html/sub03/030602.html)
- [Stony Brook AMS undergraduate course listings](https://www.stonybrook.edu/sb/bulletin/current-fall24/courses/ams/)
- [Stony Brook MAT undergraduate course listings](https://www.stonybrook.edu/sb/bulletin/current-fall24/courses/mat/)

_Roadmap reviewed July 22, 2026. Students should recheck current offerings and
prerequisites before planning an individual semester._
