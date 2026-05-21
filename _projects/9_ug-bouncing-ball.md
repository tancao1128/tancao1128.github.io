---
layout: page
title: "UG: Bouncing Ball in a Moving Polygon"
description: Implement a ball constrained to live inside a deforming polygon using only linear algebra — and discover, along the way, that you've coded a sweeping process.
img: assets/img/9.jpg
importance: 6
category: undergraduate
---

### Project at a glance

| | |
|---|---|
| **Level** | Undergraduate (AMS 487) |
| **Prerequisites** | Multivariable calculus, linear algebra (inner products, projections), some Python |
| **Effort** | Half semester (~3–4 hrs/week) |
| **Skills gained** | Geometric projections, simulation of constrained dynamics, scientific visualization, technical writing |
| **Online companion** | MIT *Matrix Calculus* (YouTube); selected chapters of Boyd & Vandenberghe *Convex Optimization* (Ch. 8 on geometric problems) |

### The big idea

You will simulate a ball moving with a prescribed velocity field $v(t)$ inside a **deforming convex polygon** $C(t)$. Whenever the ball tries to exit, you "catch it up" by projecting it back onto $C(t)$.

This sounds simple — and the code is. But what you'll have built is, mathematically, a **discrete sweeping process**: the same object whose continuous-time analysis appears in my research.

### Suggested milestones

1. **Week 1 — Half-plane projection.** Derive and implement the projection of a point $x \in \mathbb{R}^2$ onto a half-plane $\{y : a^\top y \le b\}$. Just inner products and one division.
2. **Week 2 — Polygon projection.** A convex polygon is the intersection of half-planes. Implement projection onto a polygon by alternating projections (Dykstra's algorithm) or QP.
3. **Week 3 — Moving polygon.** Parameterize $C(t)$ by a smooth family (shrinking square, rotating triangle, translating hexagon). Animate $C(t)$ over time.
4. **Week 4 — Catching-up.** At each time step $t_k = k h$, update $x_{k+1} = \text{proj}_{C(t_{k+1})}(x_k + h\, v(t_k))$. Animate the trajectory.
5. **Week 5 — Experiments.** Vary the velocity field and the deformation pattern. When does the ball stay strictly inside? When does it slide along the boundary?
6. **Week 6 — Report.** Short write-up (5–8 pages) with figures, derivations, and a one-paragraph reflection on what changes when $C(t)$ becomes nonconvex.

### Why it matters — the bridge to research

What you've coded is a **finite-difference discretization of Moreau's sweeping process**

$$
\dot x(t) \in -N_{C(t)}\bigl(x(t)\bigr) + v(t),
$$

where $N_{C(t)}(x)$ is the normal cone to the moving set $C(t)$ at $x$. In my research with B.S. Mordukhovich, G. Colombo, D. Nguyen, and others, we prove **convergence of exactly this scheme** as $h \to 0$, derive **necessary optimality conditions** when $v$ is itself a control variable, and extend the theory to nonconvex $C(t)$ — which requires the Mordukhovich coderivative.

In other words: **you've built the numerical engine; my research provides the analytical guarantees**. That gap — between a working simulation and a rigorous theorem — is exactly what graduate study in this area is about.

### Bonus directions

- Make $C(t)$ **nonconvex** (e.g., an annulus). What goes wrong? When does projection become non-unique?
- Add a **second ball** with non-overlap constraint — you've now built a 2-agent crowd-motion simulator.
- Treat $v$ as a **control**: minimize $\int_0^T |v(t)|^2\,dt$ subject to reaching a target. This is the **catching-up + optimal control** problem from my JDE papers.
