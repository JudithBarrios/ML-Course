# Lab 07 — IIoT Network Analysis: Age of Information

**Course:** ITAI 3377  
**Tool:** Google Colab

---

## What This Lab Was About

This lab looked at Age of Information (AoI) in IIoT networks — a way of measuring how old the data at the receiving end actually is at any given moment. It's different from latency or throughput. A network can look perfectly healthy by those measures and still be feeding a controller outdated information.

I worked with a simulated dataset of 10,000 records and used machine learning to try to predict AoI and Packet Loss Probability (PLP).

---

## Dataset

- 10,000 total records
- 1,397 had infinite AoI (packets never arrived) and were removed
- 8,603 records used for machine learning

---

## What I Found in the Data

Sending more often doesn't just lower AoI like you'd expect. At low rates, AoI is high because updates are rare. But at high rates, too many devices compete for the channel, more messages collide, and AoI goes back up. More transmissions can actually make things worse.

Channel quality had the strongest relationship with AoI out of any variable. The worst AoI values almost always showed up when channel quality was poor AND there were a lot of devices competing at the same time.

---

## Machine Learning Results

**Random Forest — AoI Prediction**

| Metric | Value |
|--------|-------|
| R² | –0.37 |
| RMSE | 1,736 time slots |

A negative R² means the model did worse than just guessing the average every time. I reported this honestly rather than glossing over it. The most likely reason is the extreme spread in AoI values. A log transformation before training probably would have helped.

Feature importances (what actually drives AoI):
1. Capture threshold — 0.448
2. Number of nodes — 0.231
3. Channel quality — 0.171
4. Transmission probability — 0.095
5. Traffic type — 0.055

**Deep Learning — PLP Prediction**

| Target | R² |
|--------|----|
| AoI | –0.20 |
| PLP | 0.91 |

PLP prediction was the standout result. R² of 0.91 is strong. It worked well because PLP stays between 0 and 1 with much less extreme variance than AoI.

---

## What I Learned

The feature importances told me more than the accuracy score did. Even with a bad R², I could see which variables actually drive network performance — and that matched the theory from the paper we were using. A bad model result can still be useful if you understand why it failed.

---

## Files

| File | Description |
|------|-------------|
| `L07_Notebook.ipynb` | Full lab notebook |
| `L07_Report.pdf` | Written summary report |
