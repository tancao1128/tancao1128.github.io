---
layout: page
title: "UG: From Lagrange Multipliers to Discrete Pontryagin"
description: Climb the ladder from constrained calculus to optimal control's necessary conditions using only multivariable calculus and a willingness to write down chain rules carefully.
img: assets/img/10.jpg
importance: 7
category: undergraduate
---

### Project at a glance

| | |
|---|---|
| **Level** | Undergraduate (AMS 487, ideally after AMS 341/361) |
| **Prerequisites** | Multivariable calculus (Lagrange multipliers), basic ODEs, Python (NumPy + `scipy.optimize`) |
| **Effort** | One semester (~4–6 hrs/week) |
| **Skills gained** | Constrained optimization, KKT conditions, discrete-time optimal control, the *language* of Pontryagin's principle, nonlinear programming |
| **Online companion** | CMU *Optimal Control and Reinforcement Learning* (YouTube — Karaman / Pavone style); Boyd & Vandenberghe *Convex Optimization* Ch. 5 (duality) |

### The big idea

Pontryagin's Maximum Principle is the crown jewel of optimal control theory — and in continuous time, its proof requires functional analysis and the calculus of variations. **In discrete time, it requires only the chain rule.**

You will climb a four-rung ladder:

1. **Lagrange multipliers** for equality-constrained minimization (calc you already know).
2. **KKT conditions** for inequality-constrained minimization.
3. **Discrete-time Pontryagin** for a finite-horizon optimal control problem.
4. **Application:** "land a rocket in $N$ steps with minimum fuel" — solve it two ways and verify they agree.

By the end, you will have *derived from scratch* the conditions that drive every modern OC solver.

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

   This is **discrete Pontryagin** — and the derivation is *just chain rule + Lagrange*.

4. **Weeks 8–10 — Rocket landing.** Discrete-time model: $h_{k+1} = h_k + v_k \Delta t$, $v_{k+1} = v_k + (u_k - g)\Delta t$, with $u_k \ge 0$ (thrust) and $h_N = 0$, $v_N = 0$. Minimize $\sum u_k$. Solve:
   - **(a)** Numerically with `scipy.optimize.minimize` (just throw the NLP at SLSQP).
   - **(b)** Analytically using your discrete Pontryagin conditions.

   Verify they give the same trajectory.

5. **Weeks 11–12 — Report.** 10–15 pages: derivations, code, plots, and a section "From discrete to continuous: what changes?"

### Why it matters — the bridge to research

Continuous-time Pontryagin's principle is what powers SpaceX trajectory optimization, autonomous vehicle planning, and the **optimal control of sweeping processes** that drives my research program. But continuous time requires:

- A *Hamiltonian* that lives in a function space.
- *Measure-valued* adjoint variables when the state is constrained.
- *Mordukhovich coderivatives* when the dynamics are nonsmooth (as in sweeping processes).

By the time you've finished this project, you will understand *exactly* what mathematical machinery is needed to make the continuous-time story rigorous — and *why* researchers spend their careers on it. Several of my papers (in *JDE*, *DCDS-B*, *JOTA*) are precisely about establishing analogs of Pontryagin's conditions for nonconvex sweeping processes — a setting where the classical proofs fail.

### Bonus directions

- **State constraints.** Add $h_k \ge 0$ (rocket can't go underground). Watch the multipliers become "active" — this is your first taste of the **complementarity** that pervades sweeping-process theory.
- **Free terminal time.** Make $N$ part of the optimization. This is the discrete version of the *variable-time* problems in my 2026 NAHS paper.
- **Continuous limit.** Take $\Delta t \to 0$ and verify your discrete adjoint converges to a smooth costate $p(t)$.
