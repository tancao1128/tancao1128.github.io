---
layout: page
title: "UG: From Gridworld MDP to Crowd Evacuation"
description: Start with the Bellman equation as a linear system on a 5×5 grid and end with a continuous-space multi-agent crowd evacuation simulator — touching every concept that bridges classical dynamic programming to modern reinforcement learning.
img: assets/img/11.jpg
importance: 8
category: undergraduate
---

### Project at a glance

| | |
|---|---|
| **Level** | Undergraduate (AMS 487, ideally after AMS 311 / 341) |
| **Prerequisites** | Probability and statistics, linear algebra (linear systems, eigenvalues), Python |
| **Effort** | One semester (~5–6 hrs/week) |
| **Skills gained** | Markov decision processes, Bellman equation, value/policy iteration, Q-learning, multi-agent simulation, scientific visualization |
| **Online companion** | Andrew Ng *Machine Learning* (Coursera, RL lectures); Sutton & Barto *Reinforcement Learning: An Introduction* (free PDF), Chapters 3–6 |

### The big idea

Three ideas, one ladder:

- A **Markov decision process** (MDP) on a small grid is just a finite Markov chain with rewards.
- The **Bellman equation** for the value function is a linear system you can solve with `numpy.linalg.solve`.
- Add multiple agents that must avoid each other and obstacles — and you've built a **discrete crowd-motion model**, the cousin of the continuous models in my research papers.

By the end, you'll see exactly where Andrew Ng's RL lectures stop and where my research starts.

### Suggested milestones

1. **Weeks 1–2 — Single-agent gridworld.** Implement a 5×5 grid with a goal, walls, and a penalty for each step. Write down the **Bellman equation** $V(s) = \max_a [R(s,a) + \gamma \sum_{s'} P(s'|s,a) V(s')]$ and solve it by **value iteration**. Visualize $V$ and the greedy policy.

2. **Weeks 3–4 — Linear-algebra Bellman.** For a fixed policy $\pi$, the Bellman equation becomes a **linear system** $V = R^\pi + \gamma P^\pi V$. Solve it by matrix inversion. Compare runtime vs. value iteration.

3. **Weeks 5–6 — Q-learning.** Implement tabular Q-learning. Show that with enough episodes, $Q$ converges to $Q^*$. Plot the learning curve.

4. **Weeks 7–8 — Multi-agent gridworld.** Add 5–10 agents. Each step, agents move toward the exit but cannot occupy the same cell. Implement a simple **priority rule** for conflict resolution. Measure average evacuation time as you vary obstacle density.

5. **Weeks 9–10 — Continuous-space extension.** Replace the grid with continuous positions in $[0,1]^2$. Agents are disks of radius $r$, exit is a small ball, obstacles are larger balls. **Project each step onto the feasible (non-overlapping) configuration** — you've now coupled this project to the *bouncing-ball* project (U1).

6. **Weeks 11–13 — Experiments + report.** Vary $N$ (number of agents), obstacle layout, agent radius. Plot evacuation time vs. $N$. Report (12–18 pages) with figures, code, and a section "What changes when we go to continuous time?"

### Why it matters — the bridge to research

Each milestone moves you one step closer to my research:

| Milestone | What you build | What I research |
|---|---|---|
| 1–2 | Bellman equation, discrete MDP | Discrete-time **HJB** equation |
| 3 | Q-learning convergence | **Reinforcement learning in nonsmooth dynamical systems** (emerging direction) |
| 4 | Discrete multi-agent grid | Discrete approximations in my *JDE* papers |
| 5 | Continuous, projected dynamics | **Planar crowd motion model** (Cao–Mordukhovich, *DCDS-B* 2019; Cao–Colombo–Mordukhovich–Nguyen, *IEEE-CSL* 2021) |

The continuous-time crowd-motion model is exactly what we analyzed in *"Applications of optimal control of a nonconvex sweeping process to optimization of the planar crowd motion model"*. Your simulator is a **discrete-time witness** to the same phenomena: agents getting stuck against obstacles, congestion at exits, optimal-flow trade-offs.

### Bonus directions

- **Learn the evacuation policy with deep RL.** Replace tabular Q-learning with DQN (`stable-baselines3`). Compare against the hand-tuned greedy policy. This bridges to project **U-Reinforcement Learning for Crowd Evacuation**.
- **Cooperative vs. competitive agents.** What if some agents block others? Connects to *bilevel sweeping control* — my paper with N.T. Khalil and F.L. Pereira.
- **Time-varying environment.** Make obstacles move (closing doors, opening corridors). You're now in the regime of **time-varying constraint sets** — the heart of sweeping processes.
