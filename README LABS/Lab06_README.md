# Lab 06 — IIoT Time-Series Temperature Forecasting

**Course:** ITAI 3377  
**Date:** March 25, 2026  
**Collaborator:** Brandy Griffin  
**Tool:** Google Colab

---

## What This Lab Was About

We worked with a real IoT temperature dataset — 97,606 readings from indoor and outdoor sensors collected between July and December 2018. The goal was to clean the data, build useful features, train a forecasting model, and see if adding synthetic data could improve the results.

---

## The Dataset

- 97,606 temperature readings
- Temperature range: 21°C – 51°C
- About 79% outdoor readings, 21% indoor
- No missing values

---

## What We Did

1. Cleaned column names and converted the datetime column to the right format
2. Sorted everything chronologically
3. Looked at how temperature changed over time and compared indoor vs outdoor averages (outdoor was consistently higher)
4. Created new features: hour of day, day of week, previous temperature value (`lag_1`), and a 3-period rolling average
5. Split 80% for training and 20% for testing — time-based, not random, so the model never sees future data during training
6. Trained a Linear Regression model
7. Generated synthetic data by adding small random noise to the original dataset, then retrained on the combined data

---

## Results

| Model | MAE | MSE |
|-------|-----|-----|
| Original | 1.52 | 7.89 |
| With synthetic data | 1.14 | 4.69 |

Adding synthetic data cut the error by about 25%, which was more than I expected for such a simple technique.

---

## What I Learned

You can't use a random split with time-series data. The model would be cheating if it trained on data from December and tested on data from August. Keeping the chronological order is the whole point.

The lag and rolling average features made the biggest difference — giving the model recent history to work with helped it pick up on patterns it couldn't see from just the time of day alone.

---

## Files

| File | Description |
|------|-------------|
| `L06_notebook.pdf` | Full lab notebook |
