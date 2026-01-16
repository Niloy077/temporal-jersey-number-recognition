# Temporal Jersey Number Recognition

This repository implements a lightweight temporal computer vision model for recognizing jersey numbers from sequences of player bounding-box images. The system produces a single, stable prediction per sequence and is designed to generalize to unseen two-digit numbers (00–99).

---

## Approach

- Each input sample is a **temporal sequence of images** corresponding to a tracked player.
- A **shared CNN** extracts visual features from each frame.
- A **GRU** aggregates features over time to improve robustness against blur and occlusion.
- The jersey number is predicted by **independent tens and ones digit classifiers**, enabling compositional generalization.

---

## Model Overview
Image Sequence
↓
Shared CNN Encoder
↓
Temporal GRU
↓
Mean Pooling
↓
Tens Digit Head (0–9)
Ones Digit Head (0–9)


---

## Example Architecture Diagram

![Model Architecture](assets/architecture_diagram.png)

*(Placeholder image path — replace with actual diagram if needed)*

---

## Dataset Structure

jersey_number/
└── sequence_id/
└── 0/
├── frame_001.jpg
├── frame_002.jpg
..
└── anchor.jpg


- Training and evaluation are performed at the **sequence level**
- `anchor.jpg` is excluded from inference

---

## Evaluation

Performance is reported using:
- Tens digit accuracy
- Ones digit accuracy
- Full-number (sequence-level) accuracy

Evaluation is performed on a **held-out test set** that remains unseen during training.

---

## Notes

- The model is intentionally lightweight (~200k parameters)
- Designed for low latency and scalability
- Temporal modeling significantly improves stability over single-frame prediction

---

## AI Usage Disclosure

AI tools were used for code scaffolding and documentation drafting. Model design, experimentation, and analysis were independently implemented.

