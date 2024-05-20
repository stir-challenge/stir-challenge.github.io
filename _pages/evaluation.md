---
layout: archive
title: "Evaluation"
permalink: /evaluation/
author_profile: true
---

The goals of the STIR challenge are to:

1.    Evaluate accuracy of tracking  and reconstruction algorithms.
2.    Motivate efficiency of algorithms for usage in clinical applications.


These will be ranked with two different means (accuracy, and latency). Participation in (2) is optional (but highly recommended) as it comes with an additional prize, see Prizes for more details. Algorithms can choose to compete in either the 2D or 3D quantification.


## Metrics

### Accuracy

We will be using $$ \delta^x_{avg} $$ (from [TAP-VID](https://tapvid.github.io/)) for ranking methods, which averages accuracy over multiple thresholds. This will be evaluated over a withheld and filtered test split for the competition.


**Accuracy metrics code to be released at:** [STIRMetrics](https://github.com/athaddius/STIRMetrics)

### Efficiency

Efficiency of models will be evaluated using the [NVIDIA Holoscan](https://docs.nvidia.com/holoscan/sdk-user-guide/index.html) platform. For participants in the efficiency challenge, we will evaluate efficiency as the average framewise latency combined with 95% latency. Methods which reach an efficient threshold, determined by a baseline (RAFT) will be viable for the efficiency prize. In short, if your method is faster than a threshold, you are good to go!

If you are interested in participating in the efficiency segment of the challenge, start experimenting with exporting your model to torchscript or onnx to enable use with Holoscan for benchmarking. [RAFT STIR](https://github.com/athaddius/RAFT_STIR) provides an example of this. More details will follow in June.

![Holoscan platform](/images/holoscan.png)

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

Cash prizes will be distributed with the following proportions for 1st, 2nd, 3rd place out of a total of 24 units. Prizes in the 3D category are also valid for 2D prizes. For example, if a method is first in 3D (compared against 3D participants) and second in 2D (against 2D and 3D participants), then they will get 9 units (6 for second 2D +3 for first place in 3D) of cash. The efficiency prize will be offered to the most accurate (according to 2D accuracy) method, either 2D or 3D, that is performant above a given threshold. The exact threshold is still in deliberation, but should be set relative (~0.5) to the latency of the RAFT-small model. For participants looking for the efficiency prize, we recommend starting with, or comparing your method to [RAFT_STIR](https://github.com/athaddius/RAFT_STIR) in performance.

### Cash Prizes Proportional Allocation

**2D**: 9, 6, 3
**3D**: 3, 2, 1

### Efficiency Prize

A hardware prize (TBD) provided by NVIDIA.
