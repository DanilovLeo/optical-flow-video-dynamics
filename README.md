# Optical Flow and Video Dynamics

## Variant B: Educational Motion-Analysis System (tracking module)

Analysis of optical-flow methods (Lucas-Kanade and Farneback) for tracking motion in video.

## Parameters

### Lucas-Kanade (Sparse)
- Max corners: 100
- Quality level: 0.3
- Min distance: 7
- Window size: 15x15
- Max pyramid level: 2
- Frames tracked: 200

### Farneback (Dense)
- Pyramid scale: 0.5
- Pyramid levels: 3
- Window size: 15
- Iterations: 3
- Poly n: 5
- Poly sigma: 1.2
- Thresholds tested: 2.0, 0.9

## Results

### Lucas-Kanade
- Initial points: 100
- Final points: 67
- Point loss: 33%
- Gradual degradation with a sharp drop at frames 100-140 (occlusions / objects leaving frame)

### Farneback
**Threshold 2.0:**
- Motion pixels: 1.6%
- Fragments: 13

**Threshold 0.9:**
- Motion pixels: 9.5%
- Fragments: 41

### Key observations

**LK strengths:**
- Stable long-term tracking
- Clear trajectory visualization
- Predictable behavior when points are lost

**LK weaknesses:**
- Points are lost over time (33% over 200 frames)
- Requires good texture / features

**Farneback strengths:**
- Full coverage of the motion field
- Detects all moving regions

**Farneback weaknesses:**
- High fragmentation (41 regions at threshold 0.9)
- Threshold sensitivity: a lower threshold captures more motion but increases noise
- Cannot distinguish real motion from noise without post-processing

### When to use

**LK when:**
- You need to track specific objects / features
- Speed matters
- Clear keypoints are available

**Farneback when:**
- Full scene-motion analysis is required
- Detection of all moving objects is needed
- Motion segmentation is required

## Conclusion

On this video (crowd motion), LK performed better thanks to stable tracking and clear
trajectories. Farneback showed high fragmentation, demonstrating its sensitivity to noise and
the need for careful threshold tuning.
