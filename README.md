# Automated Identification of Gait Abnormalities (Mini-Project)

**Problem statement:**  
Gait abnormalities indicate several neuromuscular conditions. Standard clinical gait analysis is expensive. We propose a low-cost video-based method to classify gait as *normal* or *abnormal* using pose estimation and machine learning.

**Approach:**  
1. **Data collection:** Short walking videos (front or side view) labeled `normal` or `abnormal`.  
2. **Preprocessing:** Use MediaPipe Pose to extract 33 body landmarks per frame. Save sequences as `.npy`.  
3. **Feature engineering:** Compute per-video statistics: vertical ranges of hip/knee/ankle, symmetry indices, motion energy, and visibility quality metric.  
4. **Modeling:** Train a RandomForest classifier on derived features. Optionally train an LSTM on raw sequences for temporal modeling.  
5. **Evaluation:** Stratified train/test split; report precision, recall, F1, confusion matrix. Use subject-wise split if multiple videos per subject exist.

**Implementation:**  
- `preprocess.py`: Extracts per-frame pose keypoints (x,y,z,visibility) and saves `.npy`.  
- `features.py`: Converts sequences to a features CSV.  
- `train.py`: Trains and saves RandomForest model (`joblib`).  
- `infer.py`: Runs inference on a held-out video.

**Results (example / expected):**  
On a small classroom dataset (~50 videos), the RandomForest classifier achieves an expected F1 in the range **0.7–0.9** depending on labeling quality and camera view. LSTM models may improve detection of temporal cues (e.g., limping) if enough training data is available.

**Challenges & Limitations:**  
- Small datasets limit deep models.  
- Pose estimation errors (occlusion, camera angle) affect features.  
- Labels may be noisy if students simulate abnormal gait.

**Future work:**  
- Replace MediaPipe with DensePose / OpenPose and explore CNN+LSTM on DensePose IUV frames (closer to Stanford paper).  
- Collect more labeled videos, add data augmentation, and evaluate subject-wise generalization.

**Repo & Run:**  
See README.md for commands to preprocess, train, and infer. Submit the private GitHub repo to faculty/TAs.

**Team:** [Your Names] — UE23CS352A Machine Learning — Submission Date: Oct 13, 2025

