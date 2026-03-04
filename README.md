# Gait Analysis using Heel Strike & Toe-Off Detection

## Overview
This project provides a Python-based gait analysis tool that processes **heel pressure** and **pitch signals** to detect key gait events, including:

- **Heel Strikes (HS)**
- **Toe-Offs (TO)**
- **Gait Phase (0–100%)**

It also computes gait metrics such as **cadence** (steps per minute) and **stride time variability** (seconds). The project is suitable for **biomechanics research, Parkinson’s gait monitoring, or wearable sensor analysis**.

---

## Features
- Adaptive threshold for heel strike detection (works for low/high amplitude signals)
- Toe-off detection as local minima between consecutive heel strikes
- Robust handling of empty or noisy signals
- Computes gait phase (0–100%) between consecutive heel strikes
- Calculates cadence and stride time variability
- Visualization:
  - Filtered pitch
  - Heel pressure with HS (red) & TO (green)
  - Gait phase over time
- Safe execution even if no heel strikes are detected

---

## Requirements
- Python 3.x
- Libraries:
  - numpy
  - pandas
  - matplotlib
  - scipy
  - google.colab (for file upload in Colab)

