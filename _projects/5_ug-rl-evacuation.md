---
layout: page
title: "UG: Reinforcement Learning for Crowd Evacuation"
description: Train an RL agent that learns to evacuate a simulated crowd from a room with obstacles in minimum time — a friendly entry point into RL and nonsmooth dynamics.
img: assets/img/5.jpg
importance: 2
category: undergraduate
---

### Project at a glance

| | |
|---|---|
| **Level** | Undergraduate (AMS 487) |
| **Prerequisites** | Python, basic probability/linear algebra; exposure to RL helpful but not required |
| **Effort** | One semester |
| **Skills gained** | Reinforcement learning, OpenAI Gym, simulation design, RL policy evaluation |

### Goal

Build a **2D grid (or continuous) crowd-evacuation simulator** and train an RL agent to learn evacuation policies that minimize average exit time.

### Suggested milestones

1. **Environment.** Implement a small evacuation simulator in `gymnasium`: a room with one or two exits, an adjustable number of pedestrians, optional obstacles.
2. **Baseline.** Compare a hand-tuned greedy policy against random behavior.
3. **RL agent.** Train DQN or PPO using `stable-baselines3`. Plot the learning curve.
4. **Analysis.** Vary the obstacle layout and crowd density; report how exit time scales.
5. **(Bonus)** Replace the discrete grid with a **continuous** model based on our planar crowd-motion sweeping-process equations.

### Why it matters

This is the small-scale, learnable cousin of the **bilevel crowd-motion sweeping control** problem in my research group. It is also great practice for the deep-RL skills that are increasingly valued in academia and industry.
