# Judith Barrios — ITAI 3377: AI at the Edge & IIoT Environments

**Course:** ITAI 3377 — AI at the Edge & IIoT Environments  
**Institution:** Houston City College  
**Instructor:** Professor Sitaram Ayyagari  
**Semester:** Spring 2026

---

## About Me

Hi, I'm Judith Barrios, a student at Houston City College studying artificial intelligence and its real-world applications. I enrolled in ITAI 3377 to deepen my understanding of how AI models are built, deployed, and used in resource-constrained environments — from edge devices and IIoT sensor networks to industrial automation systems.

Before this course, I understood AI mostly from a training perspective. This class pushed me to think about what happens *after* training: how models get compressed and deployed on hardware with limited memory, how sensor networks communicate, and how to evaluate a system's performance honestly even when the results are not perfect. That shift in perspective has been the most valuable thing I've taken away.

---

## Repository Structure

```
Judith-Barrios-ML-Course/
├── README.md
├── Labs/
│   ├── Lab02/   — TensorFlow Lite & MNIST Edge Deployment
│   ├── Lab03/   — CNN Model Deployment on Simulated Edge Device
│   ├── Lab04/   — IIoT Protocol Simulation (MQTT, CoAP, OPC UA)
│   ├── Lab06/   — IIoT Time-Series Temperature Forecasting
│   └── Lab07/   — IIoT Network Analysis: Age of Information
└── Assignments/
    ├── A03/     — Edge Computing Video Analytics Case Study
    ├── A04/     — IIoT Protocol Lab Reflective Journal
    ├── A06/     — Group Presentation
    ├── A09/     — Autonomous Agents in Industry 4.0
    └── Midterm/ — Cybersecurity Plan for AI-Integrated IIoT Healthcare System
```

---

## Labs Completed

| Lab | Topic | Key Tools |
|-----|-------|-----------|
| [Lab 02](./Labs/Lab02/) | TensorFlow Lite — Training & Edge Deployment | TensorFlow, TFLite, MNIST |
| [Lab 03](./Labs/Lab03/) | CNN Model Deployment on a Simulated Edge Device | TensorFlow, TFLite, Google Colab |
| [Lab 04](./Labs/Lab04/) | IIoT Protocol Simulation (MQTT, CoAP, OPC UA) | Python, paho-mqtt, aiocoap, asyncua |
| [Lab 06](./Labs/Lab06/) | IIoT Time-Series Temperature Forecasting | pandas, scikit-learn, matplotlib |
| [Lab 07](./Labs/Lab07/) | IIoT Network AoI & Reliability Analysis | Random Forest, Deep Learning, pandas |

---

## Assignments Completed

| Assignment | Topic |
|------------|-------|
| [A03](./Assignments/A03/) | Edge-Computing Video Analytics for Smart City Traffic Monitoring |
| [A04](./Assignments/A04/) | IIoT Protocol Lab — Reflective Journal (Group) |
| [A06](./Assignments/A06/) | Group Presentation |
| [A09](./Assignments/A09/) | Autonomous Agents in Industry 4.0 — Case Study Analysis |
| [Midterm](./Midterm/) | Cybersecurity Plan for an AI-Integrated IIoT Healthcare System |

---

## Key Takeaways from This Course

- Deploying an AI model is a completely different challenge from training one. Getting a model to run efficiently on a device with limited memory requires thinking about format, size, and inference speed — not just accuracy.
- How you design a reward function matters as much as the algorithm. This lesson from the reinforcement learning case study applies far beyond robotics.
- Sensor networks have real tradeoffs that no single metric captures. Age of Information taught me that a network can look healthy by traditional measures and still be feeding stale data to the controller.
- Bugs are part of the learning process. Every protocol in Lab 04 broke in a different and instructive way.
