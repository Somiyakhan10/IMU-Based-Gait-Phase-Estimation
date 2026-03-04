Gait Analysis using Heel Strike & Toe-Off Detection
Overview

This project provides a Python-based gait analysis tool that processes heel pressure and pitch signals to detect key gait events, including Heel Strikes (HS) and Toe-Offs (TO), and computes the gait phase (0–100%), cadence, and stride variability. The code is robust for signals of varying amplitude and includes visualizations to validate gait events.

It is particularly suitable for applications like Parkinson’s gait monitoring, biomechanics research, or wearable sensor analysis.

Features

Detect Heel Strikes (HS) using adaptive threshold and peak prominence.

Detect Toe-Offs (TO) as local minima between consecutive heel strikes.

Compute gait phase normalized from 0–100%.

Calculate cadence (steps per minute) and stride variability.

Robust handling of low-amplitude or noisy signals.

Visualization of:

Filtered pitch

Heel pressure with HS and TO

Gait phase over time

Safe execution even if no heel strikes are detected.

Requirements

Python 3.x

Libraries:

numpy

pandas

matplotlib

scipy

google.colab (for Google Colab upload functionality)
