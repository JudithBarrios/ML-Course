# Lab 03 — CNN Deployment on a Simulated Edge Device

**Course:** ITAI 3377  
**Date:** February 7, 2026  
**Tool:** Google Colab

---

## What This Lab Was About

This was a follow-up to Lab 02 but with a stronger model. Instead of a basic dense network, I built a CNN (Convolutional Neural Network) to classify MNIST digits, then converted it to TensorFlow Lite and validated it using the TFLite interpreter.

---

## Model I Built

| Layer | Details |
|-------|---------|
| Conv2D | 32 filters, 3×3 kernel, ReLU |
| MaxPooling2D | 2×2 |
| Flatten | — |
| Dense | 128 neurons, ReLU |
| Output | 10 neurons, Softmax |

---

## Results

| Metric | Value |
|--------|-------|
| Test Accuracy | 98.63% |
| Test Loss | 0.0446 |
| Epochs | 5 |
| Sample check (5 images) | 5/5 correct |

---

## What I Learned

The CNN did better than the simple dense model from Lab 02. Convolutional layers pick up on spatial patterns in images — edges, shapes, curves — before the dense layers classify them. That's why CNNs are the standard approach for image tasks.

What surprised me was how clean the TFLite conversion was. A model trained in full TensorFlow converted without any accuracy loss on the validation samples. Running through that full pipeline — train, convert, test — made it feel real in a way that just reading about it doesn't.

---

## What Was Hard

- Reshaping the images correctly for the CNN (grayscale needs a channel dimension added)
- Understanding what MaxPooling actually does to the spatial dimensions
- Making sure the TFLite output matched the original model

---

## Files

| File | Description |
|------|-------------|
| `L03_NoteBook.ipynb` | Full lab notebook |
| `L03_Report.docx` | Written report |
| `L03_ReflectiveDoc.docx` | Personal reflection |
