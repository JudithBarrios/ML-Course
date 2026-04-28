# Midterm — Cybersecurity Plan for an AI-Integrated IIoT Healthcare System

**Course:** ITAI 3377  
**Group:** Group 5  
**Submitted by:** Judith Barrios

---

## The Problem

Hospitals are one of the most targeted industries for cyberattacks, and the stakes are higher than in most sectors — a breach doesn't just expose data, it can affect patient safety directly. This project designed a cybersecurity plan for a hypothetical hospital patient monitoring network where connected devices (monitors, infusion pumps, wearables) feed into an AI system that helps doctors make faster decisions.

The challenge was treating it like a real threat model — not just listing best practices, but going through the system layer by layer and finding where it was actually vulnerable.

---

## System Overview

- Medical IoT devices: ECG monitors, smart pumps, wearable patches, glucose monitors, portable imaging
- Edge gateways in each ward
- Hospital Wi-Fi and wired network
- Electronic Health Records platform
- Four AI models: sepsis prediction, X-ray analysis, medication dosing, patient deterioration detection
- Staff devices: laptops, tablets, phones

---

## Vulnerabilities Found (15 Total)

The biggest ones:

- Default passwords still active on medical devices
- Unpatched firmware with known remote code execution vulnerabilities
- Patient data sent over MQTT with no encryption
- Patient records not encrypted at rest — a direct HIPAA violation
- SQL injection exposure in the EHR web portal
- No network segmentation, so one compromised device could reach everything else
- AI training pipeline open to data poisoning attacks
- Adversarial inputs that could fool diagnostic AI (like a modified X-ray causing a wrong diagnosis)

---

## Defense Plan

The approach was defense-in-depth — no single control is relied on. If one layer fails, others catch what gets through.

| Area | Controls |
|------|---------|
| Devices | Remove default credentials, secure boot, hardware security modules |
| Authentication | MFA, role-based access, device certificates |
| Encryption | TLS 1.3 on all connections, AES-256 for stored data |
| Network | VLAN segmentation, IDS/IPS, rogue access point detection |
| AI models | Input validation, differential privacy in training, access logging |
| Incident response | Defined playbooks, air-gap capability during active attacks |
| Compliance | HIPAA, HITECH, IEC 62443 |
| Staff | Phishing simulation, security awareness training |

---

## What I Learned

Building a threat model from scratch changed how I think about system design. The most dangerous vulnerabilities on the list — default passwords, unencrypted traffic — aren't exotic attacks. They're basic failures that happen when security isn't built in from the start.

The AI-specific vulnerabilities were the most interesting to research. Adversarial inputs and data poisoning don't exist in traditional software. They're unique to ML systems, and defending against them requires a different way of thinking about what "compromised" even means.

---

## Files

| File | Description |
|------|-------------|
| `MT_JudithBarrios_Group5_ITAI_3377.docx` | Full cybersecurity plan |
