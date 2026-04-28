# Assignment 03 — Edge Computing for Smart City Traffic Monitoring

**Course:** ITAI 3377  
**Date:** January 28, 2026

---

## The Problem

Liverpool, UK was seeing more foot and vehicle traffic as the city grew, but collecting reliable movement data the traditional way was expensive and raised privacy concerns. They had existing CCTV cameras they weren't fully using, but sending raw video to a central server would have created both bandwidth and privacy problems.

The question was: can you use the cameras you already have to gather useful planning data without ever storing or sending actual footage?

---

## How They Solved It

The system ran on an **NVIDIA Jetson TX2** — a small device with enough GPU power for real-time processing. Object detection used **YOLO V3**, and the **SORT algorithm** tracked detected objects across frames to count movement.

Everything was processed locally at the camera. Only summarized outputs — counts, movement paths — were ever transmitted. No raw video left the device.

---

## Results

- Detection accuracy: ~69% on average
- Processing speed: ~20 frames per second
- System stayed stable over long deployments
- Used in real locations: a building during a fire alarm (confirmed everyone evacuated) and Liverpool city center for pedestrian and vehicle tracking

---

## My Take

69% accuracy isn't perfect, but for urban planning it's enough to see trends reliably. The more impressive result is that the system ran stably over extended deployments — that matters more than peak accuracy in a real-world setup.

The privacy angle is also worth noting. Processing everything locally and only transmitting summaries is a genuinely better approach than sending video to a central server, and it's not a tradeoff — it's just a smarter architecture.

---

## Files

| File | Description |
|------|-------------|
| `A03_Judith_Barrios_ITAI_3377.docx` | Full written case study |
