# Capstone Project — Autonomous Maintenance Agent for a Smart Factory

**Course:** ITAI 3377  
**Type:** Conceptual Design Project  
**Due:** April 29, 2026  
**Submitted by:** Judith Barrios

---

## What This Project Is About

Factories lose a lot of money when machines break down without warning. Most places still run on fixed maintenance schedules that have nothing to do with how the equipment is actually doing — so money gets spent on machines that are fine while ones that are struggling go unnoticed.

This project is a conceptual design for an AI agent that watches over factory equipment around the clock, reads live sensor data, and takes action on its own when it spots warning signs — before a breakdown happens. The goal is fewer unplanned shutdowns, lower repair costs, and less risk for workers.

---

## How the System Is Designed

The setup follows an edge-first approach. Sensors on each machine track vibration, temperature, motor current, pressure, and rotation speed. That data goes over MQTT to a local edge gateway on the factory floor, where the AI model runs locally and makes decisions in milliseconds — no internet connection needed.

When the model spots a problem, the decision layer figures out how serious it is and picks the right response: send an alert to a cloud dashboard, trigger a control action on the machine, or log it for review. The cloud only handles long-term tracking and manager reports — not real-time decisions.

---

## The AI Side

**Anomaly Detection — Autoencoder**
The detection model is an autoencoder. It learns what normal looks like from long stretches of healthy operating data, and flags anything it can't reconstruct cleanly as a possible issue. It gets converted to TensorFlow Lite to run fast on the low-power edge device.

**Synthetic Data — GAN**
Real equipment failures are too rare to build a good training set from alone. A GAN fills that gap by generating realistic pre-failure sensor sequences. The generator creates fake readings that look like early warning signs, and through training it keeps improving until its output is realistic enough to be useful.

**Decision Logic**
The agent combines rule-based triggers (like a hard temperature limit) with a reinforcement learning policy for less urgent calls. The RL side improves over time as it gets feedback on whether its suggestions were right.

---

## Security and Ethics

- TLS encryption on all communication between sensors, edge, and cloud
- Device certificates so only verified hardware can connect
- Role-based access on the dashboard
- Network traffic monitoring

The two biggest ethical risks are false positives (sending a technician to a machine that's fine) and false negatives (missing a real warning). Both come down to training data quality. The GAN-generated data might only cover a narrow range of failure types, creating blind spots — which is why retraining on real data as it builds up is the most important long-term habit.

---

## What I Learned From This

The hardest part of this design was how much it depends on made-up training data. A GAN is a reasonable workaround for rare failure events, but the agent could end up learning artificial patterns instead of understanding how equipment actually wears down. There's no perfect fix for that at the design stage — the system has to get better over time as real data comes in.

The edge vs. cloud tradeoff also required a lot of thought. More on the edge means faster responses, but the device has limited power. The practical answer is to keep the deployed model lean and save heavier tasks like retraining for the cloud.

The most useful thing I took away from this whole project: planning for what goes wrong matters more than picking the right tools.

---

## Files

| File | Description |
|------|-------------|
| `CP_JudithBarrios_ITAI_3377_ConceptualDoc.docx` | Full conceptual design document |
| `CP_JudithBarrios_ITAI_3377_Presentation.pptx` | Presentation slides |
