---
layout: archive
title: "Evaluation"
permalink: /evaluation/
author_profile: true
---

The goals of the STIR Challenge 2025 are:

1.   _Accuracy:_ Evaluate accuracy of tracking  and reconstruction algorithms.
2.   _Efficiency:_ Motivate efficiency of algorithms for usage in clinical applications.

These will be ranked with two different means (accuracy, and latency). Participation in (2) is optional (but highly recommended) as it comes with an additional prize, of an IGX Orin Developer Kit (see Prizes for more details). Algorithms can choose to compete in either the 2D or 3D quantification.

## Metrics

### Accuracy

We will be using $$ \delta^x_{avg} $$ (from [TAP-VID](https://tapvid.github.io/)) for ranking methods, which averages accuracy over multiple thresholds. This will be evaluated over a withheld and filtered test split for the competition. The 2D metric is averaged over accuracy thresholds of [4, 8, 16, 32, 64] pixels. The 3D metric is averaged over accuracy thresholds of [2, 4, 8, 16, 32] millimetres.


**Accuracy metrics code is available at:** [STIRMetrics](https://github.com/athaddius/STIRMetrics)

### Efficiency
Refer to synapse: https://www.synapse.org/Synapse:syn65877821/wiki/631534

## Algorithm Specification

### 2D Streaming
See [STIRMetrics](https://github.com/athaddius/STIRMetrics) for reference streaming implementations of MFTs, RAFT, and CSRT. A streaming algorithm takes as input a point (or set of points), $$ x $$, image $$ I_t $$, and next image $$ I_{t+1} $$: $$ x_{t+1} = f(I_t, I_{t+1}, x) $$. The algorithm will repeatedly be run frame by frame until the end of the sequence. The algorithm may maintain a state history (e.g. previous images and points). This will be evaluated on left images.

The evaluation starts with $$ x_0 $$ and will stop at the last frame for each clip, $$ x_T $$.

### 3D Streaming

This is the same problem, but with an additional dimension in input $$ x^{3D} $$. Each algorithm, $$ f $$ is defined as a function that estimates the next image given a current stereo pair, the next stereo pair, and calibration information:
$$ x_{t+1}^{3D} = f(I^{left}_t, I^{right}_t, I^{left}_{t+1}, I^{right}_{t+1}, K, Q, x^{3D}_t) $$
Where $$ K $$ is the camera intrinsic matrix of the left camera and $$ Q $$ is the opencv backprojection matrix, $$ Q $$.

Code for algorithm evaluation in [STIRMetrics](https://github.com/athaddius/STIRMetrics) will be uploaded in June with evaluation code for 3D algorithms. For the meantime, the [STIRLoader](https://github.com/athaddius/STIRLoader) supports loading data from STIR along with K and Q, look at the dataloader used in STIRMetrics and modify it accordingly.

### Non-Streaming

Algorithms which ingress full video sequences do not have provided reference implementations currently, but are welcomed in the challenge if they modify their API to store their hidden state, and take in the framewise inputs, similar to the above 2D streaming example.


## Prizes
Refer to synapse: https://www.synapse.org/Synapse:syn65877821/wiki/631534
