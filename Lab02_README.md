# Lab 02 — TensorFlow Lite: Training & Edge Deployment

**Course:** ITAI 3377  
**Date:** January 28, 2026  
**Tool:** Google Colab

---

## What This Lab Was About

This lab introduced the full pipeline of deploying an AI model to an edge device. Starting from scratch, I trained a simple neural network on the MNIST handwritten digits dataset, saved it, converted it to TensorFlow Lite format, and ran inference using the TFLite interpreter — simulating the same process used on real edge hardware like smartphones, Raspberry Pi devices, and smart cameras.

## Steps Completed

1. **Environment Setup** — Verified Python and TensorFlow installation in Google Colab
2. **Data Loading & Normalization** — Loaded MNIST dataset and scaled pixel values from 0–255 to 0–1
3. **Model Architecture** — Built a Sequential model: Flatten → Dense(128, ReLU) → Dense(10, Softmax)
4. **Training** — Trained for 5 epochs using the Adam optimizer and sparse categorical crossentropy loss; accuracy improved each epoch, reaching ~98% validation accuracy
5. **Saving** — Saved the trained model as `mnist_model.h5`
6. **TFLite Conversion** — Converted the model to `mnist_model.tflite` using `TFLiteConverter`
7. **TFLite Inference** — Loaded the `.tflite` model using `tf.lite.Interpreter`, allocated tensors, ran inference on a test image, and compared predicted vs. actual label (result: Predicted 7, Actual 7)

## What I Learned

Before this lab, I only thought about training models. I did not realize how important the conversion step is. TensorFlow Lite showed me that models must be optimized and reformatted before they can run on devices with limited memory and power.

The biggest conceptual challenge was understanding the difference between TensorFlow and TensorFlow Lite. TensorFlow is for building and training; TFLite is for deploying on edge hardware. I also had to pay close attention to input shapes and data types — making sure the test image was reshaped and cast to `float32` before inference.

## Challenges

- Distinguishing between the TFLite Interpreter steps (allocate tensors → set input → invoke → get output) — it felt confusing until I ran through it carefully
- Matching the input tensor shape exactly to avoid silent errors
- Understanding why `.tflite` format is smaller and faster: it removes training-only components and uses a flatbuffer format optimized for inference

## Files

| File | Description |
|------|-------------|
| `notebook.ipynb` or `notebook.pdf` | Full lab notebook with code and outputs |
| `report.pdf` | Written lab report |
| `reflective_journal.pdf` | Personal reflection on learning |
