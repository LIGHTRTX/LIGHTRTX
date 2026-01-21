# Real-Time Multi-Camera Tracking System

This repository implements a real-time computer vision tracking system designed to maintain stable identities under occlusion, camera motion, and real-world noise.

The system is built for continuous inference, not demos.

---

## Problem

Most tracking systems perform well on short clips but fail in production due to:
- occlusion and partial visibility
- camera jitter and motion blur
- identity drift over long sequences
- unstable FPS under load

This project focuses on reliability, not just detection accuracy.

---

## System Overview

- Detector: YOLOv8
- Tracker: ByteTrack
- Identity Association: Appearance embeddings + temporal consistency
- Inference Mode: Real-time video stream
- Target Throughput: 95–120+ FPS

Designed to support single and multi-camera setups.

---

## Performance Metrics

Measured on real video input:

- Throughput: 110+ FPS (sustained)
- Per-frame latency: <15 ms
- ID switch reduction under occlusion: ~40%
- Cross-camera identity stability improvement: ~32%

Metrics are logged during runtime.

---

## Failure Modes Observed

The following issues were explicitly analyzed:
- long occlusion gaps
- overlapping players
- fast camera pans
- partial detections

Mitigations include confidence gating, temporal smoothing, and association tuning.

---

## How to Run

```bash
python main.py --source video.mp4
