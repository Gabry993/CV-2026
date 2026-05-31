# Histopathology WSI Registration Across Different Stains

Computer Vision course project implementing a complete histopathology image registration pipeline for Whole Slide Images (WSI) acquired with different stainings.

Checkout the [poster](poster_compressed.pdf)

![Poster JPEG](poster_compressed.jpg)

You can also visualize the notebooks results directly if you can't run them, check the 
[HTML](code_with_openslide.html)

---

## Overview

This project implements a registration pipeline for histopathology WSIs across different stains.

The pipeline includes:

- Tissue masking and preprocessing
- Multi-resolution WSI handling
- Feature extraction with SuperPoint
- Feature matching with LightGlue
- RANSAC-based similarity registration
- Dense non-rigid registration using displacement field optimization
- Registration visualization utilities:
  - overlays
  - checkerboards
  - deformation fields
  - warped grids
- Full-resolution pyramidal TIFF export

The goal is to align two histopathology slides showing the same tissue section but stained differently.

---

## Repository Structure

The repository provides **two notebooks**.

### 1. Notebook without WSI dependencies (recommended)

This notebook loads pre-exported NumPy arrays instead of directly reading WSI files.

It contains:
- preprocessing
- feature matching
- rigid registration
- non-rigid registration
- visualization
- deformation field optimization

This is the recommended notebook to run.

---

### 2. Full WSI notebook

This notebook also includes:
- OpenSlide WSI reading
- multi-resolution pyramid inspection
- full-resolution export using PyVips

However, installing:
- OpenSlide
- PyVips

can be somewhat platform-dependent and occasionally difficult.

For this reason, I do not provide detailed setup instructions for this notebook.

The registration results are identical to the lightweight notebook: the only difference is that images are read directly from WSI files instead of pre-saved NumPy arrays.

---

## About the Data

The original WSI files are extremely large and cannot be shared directly in this repository.

To make the project runnable on GitHub, I provide:
- pre-exported NumPy RGB arrays
- split into multiple smaller files to satisfy GitHub file size limits

The notebook automatically reconstructs and loads them.

---

# Quick Setup (Recommended Notebook)

## Create Python virtual environment

### Linux / macOS

```bash
python3 -m venv venv
source venv/bin/activate
```

### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

---

## Install dependencies

```bash
pip install \
numpy \
matplotlib \
opencv-python \
torch \
torchvision \
kornia \
lightglue \
scikit-image \
imageio \
imageio-ffmpeg \
tqdm
```

---

## Run Jupyter

```bash
pip install notebook
jupyter notebook
```

Then open the lightweight notebook.

---

## Notes

- The project was developed mainly for educational and research purposes.
- The implementation focuses on clarity and reproducibility rather than maximum performance.
- The code is a reimplementation of a modern histopathology registration approach: [RegWSI](https://arxiv.org/abs/2404.13108).

---
