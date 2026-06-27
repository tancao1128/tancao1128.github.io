---
layout: page
title: "UG: From Lagrange Multipliers to Discrete Pontryagin"
description: Climb the ladder from constrained calculus to optimal control's necessary conditions using only multivariable calculus and a willingness to write down chain rules carefully.
img: assets/img/10.jpg
importance: 7
category: undergraduate
---

### Project at a glance

|                      |                                                                                                                                                                                                |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Level**            | Undergraduate (AMS 487, ideally after AMS 341/361)                                                                                                                                             |
| **Prerequisites**    | Multivariable calculus (Lagrange multipliers), Python (NumPy + `scipy.optimize`). _The discrete core needs only the chain rule; ODEs appear only in the optional continuous-limit discussion._ |
| **Effort**           | One semester (~4–6 hrs/week)                                                                                                                                                                   |
| **Skills gained**    | Constrained optimization, KKT conditions, discrete-time optimal control, the _language_ of Pontryagin's principle, nonlinear programming                                                       |
| **Possible outcome** | A 10–15 page report; and, if the optional Phase 2 goes well, a note suitable for an undergraduate research venue such as SIURO.                                                                |
| **Online companion** | CMU _Optimal Control and Reinforcement Learning_ (YouTube — Karaman / Pavone style); Boyd & Vandenberghe _Convex Optimization_ Ch. 5 (duality)                                                 |

### The big idea

Pontryagin's Maximum Principle is the crown jewel of optimal control theory — and in continuous time, its proof requires functional analysis and the calculus of variations. **In discrete time, it requires only the chain rule.**

You will climb a four-rung ladder:

1. **Lagrange multipliers** for equality-constrained minimization (calc you already know).
2. **KKT conditions** for inequality-constrained minimization.
3. **Discrete-time Pontryagin** for a finite-horizon optimal control problem.
4. **Application:** "land a rocket in $N$ steps with minimum fuel" — solve it two ways and verify they agree.

By the end, you will have _derived from scratch_ the conditions that drive every modern OC solver.

### Suggested milestones

1. **Weeks 1–2 — Lagrange refresher.** Solve $\min f(x,y)$ subject to $g(x,y) = 0$ for several textbook problems. Verify numerically that $\nabla f = \lambda \nabla g$ at the optimum.

2. **Weeks 3–4 — KKT.** Extend to $\min f(x)$ s.t. $g_i(x) \le 0$. Implement a small interior-point solver, or use `scipy.optimize` with constraints. Verify complementary slackness.

3. **Weeks 5–7 — Discrete Pontryagin.** Consider the problem

   $$
   \min_{u_0,\ldots,u_{N-1}} \sum_{k=0}^{N-1} L(x_k, u_k) + \Phi(x_N), \quad x_{k+1} = f(x_k, u_k),\ x_0 \text{ given}.
   $$

   Form the Lagrangian, introduce adjoint variables $p_k$, and derive:
   - **State equation:** $x_{k+1} = f(x_k, u_k)$.
   - **Costate equation:** $p_k = \nabla_x L + (\nabla_x f)^\top p_{k+1}$.
   - **Stationarity:** $\nabla_u L + (\nabla_u f)^\top p_{k+1} = 0$.

   This is **discrete Pontryagin** — and the derivation is _just chain rule + Lagrange_.

4. **Weeks 8–10 — Rocket landing.** Discrete-time model: $h_{k+1} = h_k + v_k \Delta t$, $v_{k+1} = v_k + (u_k - g)\Delta t$, with $u_k \ge 0$ (thrust) and $h_N = 0$, $v_N = 0$. Minimize $\sum u_k$. Solve:
   - **(a)** Numerically with `scipy.optimize.minimize` (just throw the NLP at SLSQP).
   - **(b)** Analytically using your discrete Pontryagin conditions.

   Verify they give the same trajectory.

5. **Weeks 11–12 — Report.** 10–15 pages: derivations, code, plots, and a section "From discrete to continuous: what changes?"

> **Checkpoint.** After the report we decide together whether to stop here with a solid project, or to continue into the optional Phase 2 below. The decision is based on the report: correct derivations, a solver you can run and modify on your own, and clear mathematical writing.

### Why it matters — the bridge to research

Continuous-time Pontryagin's principle is what powers SpaceX trajectory optimization, autonomous vehicle planning, and the **optimal control of sweeping processes** that drives my research program. But continuous time requires:

- A _Hamiltonian_ that lives in a function space.
- _Measure-valued_ adjoint variables when the state is constrained.
- _Mordukhovich coderivatives_ when the dynamics are nonsmooth (as in sweeping processes).

By the time you've finished this project, you will understand _exactly_ what mathematical machinery is needed to make the continuous-time story rigorous — and _why_ researchers spend their careers on it. Several of my papers (in _JDE_, _DCDS-B_, _JOTA_) are precisely about establishing analogs of Pontryagin's conditions for nonconvex sweeping processes — a setting where the classical proofs fail.

### From project to a small result _(optional Phase 2)_

The discrete Pontryagin conditions themselves are classical, so the route to a publishable note is not a new theorem but a clean, verifiable case study built on your rocket-landing solver:

1. **A self-contained artifact.** Package the derivation and a reproducible two-way solver (direct NLP vs. Pontryagin) for a small family of soft-landing problems.
2. **Discrete-to-continuous costate limit.** Show empirically that the discrete adjoint $p_k$ converges to the continuous costate $p(t)$ as $\Delta t \to 0$, and estimate the rate — the optimal-control analogue of a convergence study.
3. **The state-constrained twist.** Add $h_k \ge 0$ and document how the multipliers switch on at the active set: where complementarity bites, how the discrete conditions read at the boundary, and what this previews about measure multipliers in continuous time. This is the small but genuine observation at the heart of the note.

**Target venue:** a short note for an undergraduate research venue such as SIURO (or _Involve_). This phase typically takes an additional term and, if you carry the bulk of the derivations, code, and writing, would be co-authored.

### Bonus directions

- **State constraints.** Add $h_k \ge 0$ (rocket can't go underground). Watch the multipliers become "active" — this is your first taste of the **complementarity** that pervades sweeping-process theory.
- **Free terminal time.** Make $N$ part of the optimization. This is the discrete version of the _variable-time_ problems in my 2026 NAHS paper.
- **Continuous limit.** Take $\Delta t \to 0$ and verify your discrete adjoint converges to a smooth costate $p(t)$.
