# 👤 Let Me In: Real-Time Face Recognition & Biometric Access

[![Python](https://img.shields.io/badge/Python-3.8%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![OpenCV](https://img.shields.io/badge/OpenCV-Computer%20Vision-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white)](https://opencv.org)
[![Algorithm](https://img.shields.io/badge/Biometrics-LBPH%20Face%20Recognizer-blue?style=for-the-badge)](https://opencv.org)
[![Haar Cascades](https://img.shields.io/badge/Detection-Haar%20Cascade%20Alt2-orange?style=for-the-badge)](https://opencv.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)

A modular real-time facial biometric identification and authentication program named **"Let Me In"**. Developed with Python 3 and OpenCV, the pipeline handles automated facial snapshot acquisition (`scanner.py`), biometric model training via Local Binary Patterns Histograms (`trainner.py`), and live webcam authentication with confidence bounding box overlays (`main.py`).

---

## 📌 Table of Contents
- [Executive Overview](#-executive-overview)
- [System Architecture](#-system-architecture)
- [Key Features](#-key-features)
- [Pipeline Workflow](#-pipeline-workflow)
- [Repository Structure](#-repository-structure)
- [Installation & Execution](#-installation--execution)
- [Author & Connect](#-author--connect)

---

## 🚀 Executive Overview
Facial recognition provides contactless, rapid biometric access control for physical security, attendance automation, and device authentication.

**"Let Me In"** provides an end-to-end computer vision architecture:
- **Dynamic Face Acquisition (`scanner.py`):** Automatically detects faces in webcam streams, crops the region of interest (ROI), normalizes resolution, and saves labeled training snapshots.
- **Model Training (`trainner.py`):** Utilizes OpenCV's **Local Binary Patterns Histograms (LBPH)** recognizer to encode invariant micro-texture patterns, serializing weights to `trainner.yml` and label mappings to `labels.pickle`.
- **Live Identification (`main.py`):** Reads continuous camera frames, locates faces using Haar Cascade Alt2 (`haarcascade_frontalface_alt2.xml`), computes biometric distance, and draws green identification boxes with live identity tags and confidence metrics.

---

## 🏗️ System Architecture

```text
       [ Webcam Video Stream ]
                  │
                  ▼
┌───────────────────────────────────┐
│     Haar Cascade Face Detection   │
│  (haarcascade_frontalface_alt2)   │
└───────────────────────────────────┘
                  │
                  ▼
┌───────────────────────────────────┐
│   Cropped Face ROI & Grayscale    │
└───────────────────────────────────┘
                  │
        ┌─────────┴─────────┐
        ▼                   ▼
┌──────────────┐     ┌──────────────┐
│  Phase 1:    │     │  Phase 2:    │
│  Scanner     │     │  Trainer     │
│  (Save Imgs) │     │  (LBPH YML)  │
└──────────────┘     └──────────────┘
                            │
                            ▼
                     ┌──────────────┐
                     │  Phase 3:    │
                     │  Live App    │
                     │  (main.py)   │
                     └──────────────┘
```

---

## 🎯 Key Features
- **Lighting & Texture Resilience:** LBPH operates by comparing pixels to neighboring cells, creating micro-texture representations that are robust to illumination shifts.
- **Lightweight Inference:** Runs seamlessly on standard CPUs and embedded hardware (such as Raspberry Pi) at 30+ FPS without requiring dedicated GPU acceleration.
- **Automated Label Encoding:** Dictionary-driven label pickle ensures simple onboarding of new subjects simply by adding a directory folder.

---

## 📁 Repository Structure
```text
├── main.py                          # Live webcam face recognition and HUD display app
├── scanner.py                       # Automated face capture tool for onboarding new faces
├── trainner.py                      # LBPH biometric model training script
├── trainner.yml                     # Trained LBPH serialized weights file
├── labels.pickle                    # Pickled subject name to integer label mappings
├── haarcascade_frontalface_alt2.xml # OpenCV Haar Cascade frontal face XML
├── requirements.txt                 # Python dependencies (opencv-python, numpy, pillow)
├── dataset/                         # Labeled subject image directories
└── file/                            # Asset images and UI icons
```

---

## 🛠️ Installation & Execution

### 1. Clone Repository & Setup
```bash
git clone https://github.com/abhik99/Face_recognition-Let_Me_In-.git
cd Face_recognition-Let_Me_In-

pip install -r requirements.txt
```

### 2. Capture Training Photos (Optional for new users)
```bash
python scanner.py
```

### 3. Train the LBPH Model
```bash
python trainner.py
```

### 4. Run Live Recognition
```bash
python main.py
```
*Press `q` on the webcam window to exit.*

---

## 👨‍💻 Author & Connect

**Abhishek Kumar (Abhi)**  
*Data Scientist & Analytics Engineer*

- 🌐 **Portfolio:** [abhicodes.online](https://abhicodes.online)
- 💼 **LinkedIn:** [linkedin.com/in/abhik99](https://linkedin.com/in/abhik99)
- 🐙 **GitHub:** [@abhik99](https://github.com/abhik99)
- 📧 **Email:** [akdevil27boy@gmail.com](mailto:akdevil27boy@gmail.com)

---
*Distributed under the MIT License.*
