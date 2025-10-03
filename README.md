# Automated Identification of Gait Abnormalities

## Overview
Simple video-based system to classify gait as **normal** or **abnormal** using pose estimation (MediaPipe) + ML.

## Repo structure
- data/                # Put your videos here (see structure)
  - normal/
  - abnormal/
- code/
  - preprocess.py      # Extracts keypoints using MediaPipe
  - features.py        # Computes per-video features
  - train.py           # Trains RandomForest or LSTM
  - infer.py           # Run inference on a video
  - utils.py           # helper functions
- models/              # saved models (created after training)
- reports/
  - one_page_writeup.md
- requirements.txt

## Quick setup
1. Create & activate virtual env (recommended).
2. `pip install -r requirements.txt`

## Data format
Place videos in:
