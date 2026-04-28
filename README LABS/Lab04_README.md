# Lab 04 — IIoT Protocol Simulation: MQTT, CoAP, and OPC UA

**Course:** ITAI 3377  
**Date:** February 14–20, 2026  
**Group:** Brandie Griffin, Michael Garcia, Judith Barrios

---

## What This Lab Was About

We built a working IIoT simulation from scratch using three real industrial protocols — MQTT, CoAP, and OPC UA — all running locally in Python. For each one, a sensor script generated fake temperature and humidity data, sent it to a server or broker, and a visualization showed the live stream.

The goal was to actually feel the difference between these protocols, not just read about them.

---

## What Each Protocol Was Like

**MQTT**
The sensor published data to a topic, the Mosquitto broker passed it along, and a subscriber displayed it live. It was the easiest of the three to get running. The problem we hit was a threading error — the MQTT callback runs on a background thread but Tkinter (the chart library) only works on the main thread. We fixed it by passing data through a queue so only the main thread touched the chart.

**CoAP**
The sensor client sent POST requests to a CoAP server every second. When it worked, the server returned `2.04 Changed OK` which was satisfying to see. The problem was port 5683 was still being held by a previous process after a restart. We had to use `netstat` to find which process had it, then `taskkill` to kill it.

**OPC UA**
This one had the steepest learning curve. OPC UA isn't just a protocol — it structures data with namespaces, types, and variable nodes. The script broke because of missing `await` keywords on async calls. Once we found that in the documentation it was a quick fix, but it took a while to find.

---

## What Each Protocol Is Actually For

- **MQTT** — lightweight, fast, good for lots of sensors sending small amounts of data constantly
- **CoAP** — like HTTP but for constrained devices, runs over UDP
- **OPC UA** — used in real industrial systems when data structure and reliability matter more than simplicity

---

## What I Contributed

I researched all three protocols before we started coding. I helped with OPC UA troubleshooting and cross-checked the asyncua documentation when the async error came up. I also wrote the learning outcomes section and the future applications part of the report.

---

## Files

| File | Description |
|------|-------------|
| `LO4SCREENSHOTS.pdf` | Step-by-step screenshots for all three protocols |
| `A04_reflective_journal.docx` | Group reflective journal |
