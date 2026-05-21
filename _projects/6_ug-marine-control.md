---
layout: page
title: "UG: Trajectory Planning for a Simulated Boat"
description: Implement and visualize a free-time optimal navigation problem for an autonomous surface vehicle avoiding circular obstacles.
img: assets/img/6.jpg
importance: 3
category: undergraduate
---

### Project at a glance

| | |
|---|---|
| **Level** | Undergraduate (AMS 487) |
| **Prerequisites** | ODEs, basic Python, willingness to learn numerical optimization |
| **Effort** | One semester |
| **Skills gained** | Constrained optimization, ODE discretization, scientific visualization |

### Goal

Recreate, in simplified form, the **marine surface vehicle navigation** problem we studied in *IEEE Control Systems Letters* — a kinematic model where a boat must reach a target while avoiding a set of forbidden zones in minimum time.

### Suggested milestones

1. **Model.** Write the boat kinematics ($\dot x, \dot y, \dot \theta$) with bounded steering control.
2. **Discretization.** Use a uniform time grid; encode the obstacle-avoidance constraint as a sweeping-process-style projection.
3. **Solver.** Solve the resulting nonlinear program with `scipy.optimize` or `pyomo + ipopt`.
4. **Visualization.** Animate the optimal trajectory under several obstacle configurations.
5. **(Bonus)** Make the terminal time a decision variable and study how the optimal time changes with obstacle density.

### Why it matters

Marine-vehicle path planning is one of the cleanest **real-world demonstrations** of sweeping-process control theory. The project produces visualizations you can put on your CV and a working solver you understand end-to-end.
