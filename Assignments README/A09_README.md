# Assignment 09 — Autonomous Agents in Industry 4.0

**Course:** ITAI 3377  
**Source:** Hjulstrom, L. (2022). KTH Royal Institute of Technology.

---

## The Problem

Traditional warehouse vehicles follow fixed paths using floor markers and a central controller. They can't adapt when things change, and the markers are expensive to maintain. This case study looked at whether reinforcement learning could make these vehicles self-directing — able to navigate and manage their own battery through trial and error.

---

## How the System Worked

Three agents operated in a simulated 10×10 grid warehouse. Each one had to carry objects between locations while watching its battery and visiting charging stations before running out of power.

The system was built in Python using TensorFlow and TF-Agents, with a Double Deep Q-Network (DDQN) algorithm.

Each agent knew four things at every step: its own position, the target location, its battery level, and what was in the four squares around it. From that it chose to move up, down, left, or right.

**Reward structure:**
- +100 for reaching a target
- –70 for hitting a wall or another agent
- –100 for running out of battery
- –1 per step (pushes toward efficiency)

Training ran for 200,000 episodes. Every 30,000 episodes the task got harder, which forced the agents to learn battery management and navigation at the same time.

---

## Results

All three agents finished all 300 tasks with zero crashes and zero battery failures. They averaged 2.59 extra steps per task beyond the shortest possible path — accounting for recharging stops and avoiding each other.

---

## Limitations

- Only tested in one fixed 2D layout — real warehouse performance is unknown
- Agents couldn't communicate with each other or check if a charging station was free
- Battery behavior was unrealistic (constant drain rate, instant recharge)

---

## My Reflection

The reward function design is the real work in reinforcement learning. How you assign points and penalties is what shapes agent behavior — get it wrong and the agent learns something useless. That lesson applies to any system that learns from feedback, not just robotics.

The paper spends about two sentences on job automation before moving on, which felt out of proportion to the actual issue. Systems like this are built to replace real work that real people do right now. The technical results deserve to be taken seriously, and so does that.

---

## Files

| File | Description |
|------|-------------|
| `A09_Judith_Barrios_ITAI3377.pdf` | Full case study and reflection |
