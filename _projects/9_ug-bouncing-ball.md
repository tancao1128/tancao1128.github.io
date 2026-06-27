---
layout: page
title: "UG: Bouncing Ball in a Moving Polygon"
description: A first undergraduate research project on projections, constrained motion, and sweeping processes, starting from linear algebra and Python.
img: assets/img/9.jpg
importance: 6
category: undergraduate
---

### Project at a glance

|                      |                                                                                                                                            |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| **Level**            | Undergraduate; suitable as a first research experience                                                                                     |
| **Prerequisites**    | Multivariable calculus, linear algebra (inner products, projections), basic Python. _No differential equations or real analysis required._ |
| **Effort**           | 4-6 week trial project, extendable to a semester                                                                                           |
| **Skills gained**    | Projections, constrained dynamics, numerical simulation, visualization, short technical writing                                            |
| **Best fit**         | Students who enjoy geometry, coding, and visual experiments                                                                                |
| **Possible outcome** | A short report; and, if the optional Phase 2 goes well, a note suitable for an undergraduate research venue such as SIURO.                 |
| **Online companion** | MIT _Matrix Calculus_ (YouTube); selected parts of Boyd & Vandenberghe, _Convex Optimization_                                              |

### The big idea

Imagine a point particle moving in the plane while a polygonal container changes with time. At each small time step, the particle first follows a prescribed velocity, and then, if it has moved outside the polygon, it is projected back into the admissible region.

The starting problem is concrete:

$$
x_{k+1}=\operatorname{proj}_{C(t_{k+1})}\bigl(x_k+h\,v(t_k)\bigr),
$$

where $C(t)$ is a moving convex polygon. This looks like a small Python simulation, but it is also the basic numerical step behind a **sweeping process**, a class of nonsmooth dynamical systems used to model constrained motion, contact, crowd motion, and state-constrained control problems.

### First task

The first assignment is deliberately small:

1. Derive the formula for the projection of a point $x\in\mathbb{R}^2$ onto a half-plane
   $$
   H=\{y\in\mathbb{R}^2: a^\top y\le b\}.
   $$
2. Implement this projection in Python.
3. Test it on several examples and plot the original point, the projected point, and the boundary line.
4. Write a short explanation of the formula and include the plots.

This first step already uses the main mathematical ideas of the project: inner products, distances, constraints, and projections.

### Suggested 4-6 week plan

1. **Week 1 — Projection onto a half-plane.** Derive, implement, test, and visualize the projection formula.
2. **Week 2 — Projection onto a polygon.** Represent a convex polygon as an intersection of half-planes. Implement projection onto simple polygons, either by alternating projections or by using a small quadratic program.
3. **Week 3 — Moving polygon.** Build examples of a time-dependent polygon: a translating square, a rotating triangle, or a slowly shrinking rectangle.
4. **Week 4 — Catching-up simulation.** Implement
   $$
   x_{k+1}=\operatorname{proj}_{C(t_{k+1})}\bigl(x_k+h\,v(t_k)\bigr)
   $$
   and animate the trajectory.
5. **Weeks 5-6 — Experiments and write-up.** Vary the time step, velocity field, and polygon motion. Observe when the particle stays in the interior, hits the boundary, or slides along an edge. Prepare a short report with formulas, code snippets, figures, and conclusions.

> **Checkpoint.** After the short report we decide together whether to stop here with a solid first project, or to continue into the optional Phase 2 below. The decision is based on the report: clean and correct code, experiments you can run on your own, and clear mathematical writing.

### Why it matters — the bridge to research

In continuous time, the corresponding model is a perturbed sweeping process,

$$
\dot x(t) \in -N_{C(t)}\bigl(x(t)\bigr) + v(t),
$$

where $N_{C(t)}(x)$ is the normal cone to the moving set at the point $x$. The projection algorithm above is a discrete version of this dynamics: it keeps the state inside the feasible set while allowing motion along the boundary.

This connects directly to my research on optimal control of sweeping processes. In that research, one studies questions such as:

- Does the discrete scheme converge to a continuous-time trajectory as $h\to 0$?
- What happens when the moving set is nonconvex?
- How should the velocity $v(t)$ be chosen if we want to reach a target while minimizing an energy or time cost?
- What optimality conditions replace the classical Pontryagin principle when the dynamics contain normal cones and state constraints?

Thus the undergraduate project starts with a simple visual simulation, but it leads naturally toward modern research in nonsmooth dynamics, variational analysis, and optimal control.

### From trial to a small result _(optional Phase 2)_

The bare simulation reproduces convergence that is _already_ known (see the research bridge above), so on its own it is not a new result. What turns it into a publishable note is one focused increment, built directly on your Phase-1 code:

1. **Exact benchmarks.** Derive closed-form trajectories for a few simple moving polygons — a square or triangle _translating_ at constant velocity (a change of variables reduces this to a fixed set), and, as a stretch goal, a regular polygon _rotating_ at constant angular velocity. These give _exact_ references to test against.
2. **Empirical order of convergence.** Measure the error $e(h)=\max_t\lVert x_h(t)-x_{\text{exact}}(t)\rVert$ and estimate the convergence order from a log–log plot, comparing it with the theoretical rates ($O(h)$, or $O(\sqrt{h})$ in weaker settings).
3. **The corner effect.** Isolate trajectories that cross or graze a _vertex_ of the polygon — exactly where the normal cone becomes multivalued — and check whether the convergence order degrades there. This small but genuine numerical observation is the heart of the note.

**Target venue:** a short note for an undergraduate research venue such as SIURO (or _Involve_). This phase typically takes an additional term and, if you carry the bulk of the code, experiments, and writing, would be co-authored.

### Possible extensions

- **Numerical analysis.** Study how the trajectory changes as the time step $h$ decreases.
- **Nonconvex sets.** Try a nonconvex region and identify where projection becomes non-unique or unstable.
- **Two particles.** Add a second particle and impose a non-overlap constraint. This gives a first toy model for crowd-motion dynamics.
- **Optimal control.** Treat $v(t)$ as a control and ask for the lowest-energy way to reach a target while staying inside $C(t)$.

### Expected output

By the end of the initial project, the student should produce:

- a short Python notebook or script;
- plots and animations of the projection and catching-up dynamics;
- a 5-8 page report explaining the projection formulas, simulation method, and main observations;
- a brief reflection on which extension would be most interesting to pursue next.
