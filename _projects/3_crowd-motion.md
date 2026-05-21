---
layout: page
title: Crowd Motion & Marine Vehicle Control
description: Optimal control of nonconvex sweeping processes applied to pedestrian dynamics, evacuation, and autonomous marine surface vehicles.
img: assets/img/3.jpg
importance: 3
category: research
related_publications: true
---

Sweeping-process control theory has powerful **real-world applications** when the state constraints encode physical non-overlap or boundary conditions. Two application threads I have pursued:

### Crowd motion models

The **planar crowd motion model** treats each pedestrian as a disk constrained not to overlap with others or with fixed obstacles. The resulting nonconvex sweeping process governs the velocity field, and the optimal-control problem seeks evacuation strategies, optimal egress paths, or congestion-minimizing flows.

- Joint work with B.S. Mordukhovich (Wayne State) and Giovanni Colombo (Padova).
- Bilevel sweeping control formulations (with N.T. Khalil and F.L. Pereira) allow leader–follower dynamics.
- Models with obstacles handled in *IEEE Control Systems Letters* (2021).

### Marine surface vehicles

Free-time / variable-time sweeping process control models the navigation of an autonomous **marine surface vehicle** that must reach a destination while avoiding obstacles (other vessels, shorelines, exclusion zones). Optimization is over both the steering control and the (free) terminal time.

- Joint work with N.T. Khalil, B.S. Mordukhovich, D. Nguyen, T. Nguyen, F.L. Pereira.
- Published in *IEEE Control Systems Letters* (2021).

### Ongoing extensions

- **Reinforcement learning** in nonsmooth dynamical systems, including policy-gradient methods for mean-variance portfolio optimization under regime-switching (with L. Vu, in preparation).
- Optimal control of ODE systems with **hysteresis** via discrete approximations.
- Robotics applications of controlled sweeping processes.
