---
layout: archive
title: "Evaluation"
permalink: /evaluation/
author_profile: true
---

The goals with the STIR challenge are to:
1. Evaluate accuracy of tracking  and reconstruction algorithms.
2. Motivate efficiency for usage in clinical applications.

Algorithms can choose to compete in either the 2D or 3D quantification.

## Format

### 2D Streaming
See [STIRMetrics](https://github.com/athaddius/STIRMetrics) for reference streaming implementations. A streaming algorithm takes as input a point (or set of points), $$ x $$, image $$ I_t $$, and next image $$ I_{t+1} $$: $$ x_{t+1} = f(I_t, I_{t+1}, x) $$. The algorithm will repeatedly be run frame by frame until the end of the sequence. The algorithm may maintain a state history (e.g. previous images and points). This will be evaluated on left images.

The evaluation starts with $$ x_0 $$ and will stop at the last frame for each clip, $$ x_T $$.

### 3D Streaming

This is the same problem, but with an additional dimension in input $$ x^{3D} $$. Each algorithm, $$ f $$ is defined as a function that estimates the next image given a current stereo pair, the next stereo pair, and calibration information:
$$ x_{t+1}^{3D} = f(I^{left}_t, I^{right}_t, I^{left}_{t+1}, I^{right}_{t+1}, K, Q, x^{3D}_t) $$
Where $$ K $$ is the camera intrinsic matrix of the left camera and $$ Q $$ is the opencv backprojection matrix, $$ Q $$.

### Non-Streaming

Algorithms which ingress full video sequences do not have provided reference implementations currently, but are welcomed in the challenge.

## Accuracy

### Metrics

**Accuracy metrics and code to be released.** See: [STIRMetrics](https://github.com/athaddius/STIRMetrics)

## Efficiency

**Efficiency will be a sub-evaluation. To-be-determined.**