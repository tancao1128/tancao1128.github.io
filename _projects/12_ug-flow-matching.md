---
layout: page
title: "UG: Flow Matching — Learning to Turn Noise into Data with ODEs"
description: Build a modern generative model from scratch using nothing but vector fields, ODEs, and a willingness to follow a particle along a straight line. A gentle on-ramp from multivariable calculus to the math behind today's image and robotics generative models.
img: assets/img/12.jpg
importance: 9
category: undergraduate
---

### Project at a glance

|                      |                                                                                                                                                                                                                                                                  |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Level**            | Undergraduate (after AMS 261 / a first ODE course; some exposure to probability helps). _Of the three undergraduate options, the most programming- and prerequisite-heavy._                                                                                      |
| **Prerequisites**    | Multivariable calculus (vector fields, the chain rule), ordinary differential equations (what it means to _solve_ $\dot x = u(x,t)$), basic probability (samples, expectations), Python (NumPy + Matplotlib; PyTorch optional)                                   |
| **Effort**           | One semester (~4–6 hrs/week)                                                                                                                                                                                                                                     |
| **Skills gained**    | Vector fields & flows, numerical ODE integration (Euler / RK4), probability paths, the (conditional) flow-matching objective, training a small neural velocity field, sampling by integration                                                                    |
| **Possible outcome** | A 10–15 page report; and, if the optional Phase 2 goes well, a note suitable for an undergraduate research venue such as SIURO.                                                                                                                                  |
| **Online companion** | Federico Sarrocco, [_Flow Matching: Matching Flows_](https://federicosarrocco.com/blog/flow-matching) (intuitive, visual, with code); Lipman et al., _Flow Matching for Generative Modeling_ (the original paper); the Meta AI _flow_matching_ library on GitHub |

### The big idea

Modern generative models — the systems that turn random noise into photorealistic images, molecules, or robot trajectories — sound like they need a graduate course in stochastic calculus. **Flow Matching shows they don't.** At its heart sits an object you already met in AMS 261: a **time-dependent vector field**

$$
u_t(x), \qquad t \in [0,1].
$$

Drop a particle into this field at a random starting point $x_0$ drawn from simple noise, and let it flow by solving the ODE

$$
\frac{d}{dt}\,\psi_t(x_0) = u_t\big(\psi_t(x_0)\big), \qquad \psi_0(x_0) = x_0.
$$

At $t = 1$ the particle lands on a sample from the _data_ distribution. **Generating data = integrating an ODE.** The only question is: _which_ vector field $u_t$ carries noise to data — and Flow Matching is a strikingly simple recipe for learning it.

The punchline that makes this an undergraduate project: although the "true" field is defined by an intractable average over all data, you can learn it by regressing on a **conditional** field whose formula is _one line_. Pick a data point $x_1$, pick noise $x_0$, draw the straight line between them,

$$
\psi_t(x_0 \mid x_1) = (1-t)\,x_0 + t\,x_1,
$$

and the velocity that traces it is simply the constant $x_1 - x_0$. Train a network $u_t^\theta$ to match that target and — remarkably — you recover the correct _global_ flow. That is the **Conditional Flow Matching** loss:

$$
\mathcal{L}(\theta) = \mathbb{E}_{t,\,x_0,\,x_1}\Big\|\,u_t^\theta\big((1-t)x_0 + t x_1\big) - (x_1 - x_0)\,\Big\|^2.
$$

No simulation during training, no divergences to compute, no adjoint ODEs — just a mean-squared-error fit. You will _derive it, code it, and watch a cloud of Gaussian noise reorganize itself into a spiral, two moons, or a hand-drawn shape._

### Suggested milestones

1. **Weeks 1–2 — Flows as ODEs.** Implement a forward Euler and an RK4 integrator for $\dot x = u(x,t)$ in 2D. Hand-design a few vector fields (rotation $\langle -y, x\rangle$, a sink, a shear) and _animate_ the particles flowing. Connect every picture back to the AMS 261 vocabulary: field, flow line, divergence.

2. **Weeks 3–4 — Probability paths by hand.** Take source = standard Gaussian, target = a fixed point, then target = a ring. Build the linear interpolation path $x_t = (1-t)x_0 + t x_1$ for many sample pairs and **histogram $x_t$ at several times** to _see_ the distribution $p_t$ morph from noise to data. Write down the conditional velocity $x_1 - x_0$ and verify numerically that integrating it reproduces the path.

3. **Weeks 5–7 — The Flow Matching loss.** Derive the Conditional Flow Matching objective above and explain, in your own words, why matching the _conditional_ field suffices (the key lemma: the conditional velocities, averaged over data, give the correct marginal field). Implement the loss for a tiny MLP velocity field $u_t^\theta(x)$ in PyTorch.

4. **Weeks 8–10 — Train and sample.** Train on a 2D toy dataset (two moons, spiral, or a point cloud sampled from a letter). **Generate** new samples by drawing noise and integrating $u_t^\theta$ from $t=0$ to $t=1$ with your RK4 solver. Plot the learned field and the trajectories. Study how step count and network size affect sample quality.

5. **Weeks 11–12 — Report + one extension.** A 10–15 page write-up: the ODE picture, the derivation, your experiments, and one of the bonus directions below. Include a section: _"Why is this just a vector field on the inside?"_

> **Checkpoint.** After the report we decide together whether to stop here with a solid project, or to continue into the optional Phase 2 below. The decision is based on the report: working and reproducible code, experiments you can run on your own, and a clear explanation of the math.

### Why it matters — the bridge to research

Flow Matching is not a toy: it is the training principle behind state-of-the-art image generators (Stable Diffusion 3), molecular design, and — closest to my own work — **generative models of robot and agent trajectories**. And the mathematics sits squarely on the themes of my research program:

- A learned velocity field driving an ODE is exactly a **control system** $\dot x = u(x,t)$. Asking _which_ field transports one distribution to another is a **distributional optimal-transport / optimal-control** question — the continuous cousin of the Pontryagin and reinforcement-learning projects elsewhere on this page.
- When the dynamics or the feasible set are **nonsmooth or constrained** (a particle that must stay inside a region, an agent in a crowd), the clean ODE becomes a **differential inclusion / sweeping process** — precisely the setting of my papers on optimal control of sweeping processes. Flow Matching is the smooth, data-driven doorway into that world.

By the end you will understand, concretely, that "AI that generates data" is _applied dynamical systems_ — and you will be holding the exact mathematical thread that leads from AMS 261 into modern research on controlling distributions.

### From project to a small result _(optional Phase 2)_

A working Flow-Matching demo reproduces known results, so the increment that makes a note is a focused, quantitative study built on your Phase-1 code:

1. **A reproducible artifact with a metric.** Train Conditional Flow Matching on 2D benchmarks (two moons, spiral) and measure sample quality _quantitatively_ — e.g. an energy distance or $2$-Wasserstein to the target — rather than by eye.
2. **One controlled comparison.** Pick a single axis and study it carefully: how the probability-path schedule (straight-line vs. a curved $\alpha_t, \sigma_t$) trades off against the number of ODE steps needed to reach a target quality.
3. **Constrained flows (research-flavored, closest to my current work).** Project the learned velocity at each step so trajectories stay inside a polygon, turning the clean ODE into a **sweeping process**; measure the feasibility-vs-quality trade-off and document what breaks. This connects directly to my active research on constrained flow matching.

**Target venue:** a short note for an undergraduate research venue such as SIURO. This phase typically takes an additional term and, if you carry the bulk of the code, experiments, and writing, would be co-authored.

### Bonus directions

- **Curved paths.** Replace the straight-line interpolation with a general schedule $\psi_t = \alpha_t x_1 + \sigma_t x_0$ and compare sample quality and trajectory shape.
- **Diffusion connection.** Show numerically that a particular choice of schedule reproduces the score / diffusion-model dynamics — the link the original Flow Matching paper makes precise.
- **Conditional generation.** Condition the field on a class label and generate from a chosen mode (e.g. only the "1"-shaped cloud).
- **Constrained flows (research-flavored).** Force the trajectories to stay inside a polygon by projecting the velocity at each step. Watch the clean ODE turn into a **sweeping process** — and write down what breaks. This is a genuine open-research direction in disguise.
