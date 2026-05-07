# GaitPhase-Analyzer — Wearable Insole Gait Analysis & Slip Risk Scoring

**Real-time gait analysis and fall risk assessment from wearable insole pressure and IMU data**

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![NumPy](https://img.shields.io/badge/NumPy-1.24+-orange.svg)
![Pandas](https://img.shields.io/badge/Pandas-2.0+-green.svg)
![SciPy](https://img.shields.io/badge/SciPy-1.10+-red.svg)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.7+-yellow.svg)
![License](https://img.shields.io/badge/License-MIT-purple.svg)

---

## ⚠️ Medical Disclaimer

> **Disclaimer:** This tool is developed strictly for **research and educational purposes**. It is NOT a certified medical device and must not be used as the sole basis for clinical decision-making. All results should be reviewed and validated by qualified healthcare professionals.

---

## 📌 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Screenshots](#screenshots)
- [How It Works](#how-it-works)
- [Input File Format](#input-file-format)
  
---

## 🔬 Overview

**GaitPhase-Analyzer** is a Python-based tool that processes raw data from wearable insoles (pressure sensors + IMU) to perform comprehensive gait analysis. It detects key gait events, estimates continuous gait phase, and calculates a **step-by-step slip risk score** — a quantitative measure of fall risk that can be used for continuous, real-world monitoring.

This tool is specifically designed for researchers working with:
- Elderly populations at risk of falls
- Parkinson's disease patients
- Stroke survivors
- Other clinical populations with gait impairments

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| **Automatic Event Detection** | Detects heel strikes (HS) and toe-offs (TO) from pressure signals |
| **Gait Phase Estimation** | Calculates continuous 0-100% phase using linear interpolation between events |
| **Slip Risk Scoring** | Computes a 0-100 risk score for each step based on 4 biomechanical metrics |
| **Gait Metrics** | Calculates cadence (steps/min) and stride time variability |
| **Adaptive Thresholds** | Automatically adjusts to individual walking patterns using percentile-based normalization |
| **CSV Auto-Detection** | Automatically identifies timestamp, pitch, and pressure columns |
| **Visual Output** | Generates professional plots for research and clinical reporting |
| **Any CSV Support** | Works with any CSV file containing pressure and pitch data |

---

## 📸 Screenshots

### Plot A - Pitch Angle from Insole IMU
<img width="1379" height="343" alt="image" src="https://github.com/user-attachments/assets/112e9be6-6674-4bd5-9c9b-da7bcf115f51" />

*Filtered IMU pitch angle showing ankle dorsiflexion/plantarflexion pattern during walking*

### Plot B - Heel Pressure with Detected Gait Events
<img width="1379" height="348" alt="image" src="https://github.com/user-attachments/assets/7fd16396-e3ca-4caf-a1b1-f4fdcddb06a2" />

*Black line shows pressure signal. Red triangles indicate heel strikes. Green triangles indicate toe-offs.*

### Plot C - Estimated Gait Phase
<img width="1379" height="375" alt="image" src="https://github.com/user-attachments/assets/a0c2970d-d0ea-48bf-86da-53c699e9c10d" />

*Purple sawtooth wave shows 0-100% gait phase. Gray dashed line shows stance/swing boundary at 60%.*

### Plot D - Slip Risk Score per Step
<img width="1379" height="386" alt="image" src="https://github.com/user-attachments/assets/7cf2f703-62e9-4b0e-ae54-c8a532bda727" />

*Color-coded bars showing risk level for each step. Green=Low, Orange=Moderate, Red=High.*

---

## ⚙️ How It Works

### Step-by-Step Pipeline
Raw CSV Data
↓
Signal Filtering (Low-pass Butterworth)
↓
Heel Strike Detection (Peak finding)
↓
Toe-Off Detection (Minima between heel strikes)
↓
Gait Phase Calculation (0% → 100% between events)
↓
Slip Risk Score Calculation per Step
↓
Visual Output (4 plots + summary statistics)

### Slip Risk Metrics

| Metric | Biomechanical Meaning |
|--------|----------------------|
| **Impact Slope** | Rate of pressure increase at heel strike (sudden impact = higher risk) |
| **Foot Flat Duration** | Time from heel strike to toe-off (shorter = unstable = higher risk) |
| **Pitch at Heel Strike** | Ankle angle at initial contact (heel-first landing = higher risk) |
| **Push-off Change** | Pitch velocity at toe-off (rapid change = loss of control = higher risk) |

---

## 📁 Input File Format

### Required Columns

Your CSV file should contain at least:

| Column | Description |
|--------|-------------|
| `timestamp` or `time` | Time in seconds or milliseconds |
| `pitch` | IMU pitch angle (degrees) |
| `p_heel_i` and/or `p_heel_o` | Heel pressure values (can be one or both) |

### Sample CSV

```csv
timestamp,pitch,p_heel_i,p_heel_o
0.000,2.5,100,150
0.010,3.2,250,200
0.020,4.1,500,450
0.030,5.0,800,700
...
 Slip Risk Score Interpretation
Score Range	Risk Level	Meaning	Recommended Action
0-30	Low	Stable gait, normal walking pattern	Continue monitoring
30-60	Moderate	Some instability detected	Observe closely, consider intervention
60-100	High	Significant fall risk	Immediate intervention recommended
===== Results =====
Total steps analyzed: 73
Average slip risk score: 35.2/100
Maximum slip risk score: 67.0/100
Minimum slip risk score: 0.0/100
Standard deviation: 18.5

Risk Level Distribution:
  Low risk (0-30): 41 steps (56%)
  Moderate risk (30-60): 25 steps (34%)
  High risk (60-100): 7 steps (10%)

Highest risk steps:
  Step 4: 67.0/100
  Step 12: 65.0/100
  Step 23: 62.0/100
