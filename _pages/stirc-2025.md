---
layout: archive
title: "STIRC 2025"
permalink: /stirc-2025/
author_profile: true
---
![MICCAI 2025 Logo](/images/miccai2025-logo.png)

# 📄 Report Paper
*TBA*

# Timeline

- **April 2, 2025** Synapse website launched
- **May 4, 2025** Webpage updated for STIRC 2025
- **May 27, 2025** Submission instructions posted
- **August 20, 2025** Submissions due
- **Late August, 2025** Report Submission Deadline
- **September 23-27, 2025** Challenge day at MICCAI 2025

# Dataset

The test dataset for STIRC2025 contains around 32 sequences. No intersection with any of the other released datasets.

*The evaluation set (STIRC2024) can be found [**here**](https://zenodo.org/records/14803158).*

## Use of External Data
Publicly available data are usable for training. Recommended datasets with deformation or tracking labels are mentioned in the prior years challenge [paper](https://arxiv.org/abs/2503.24306)<sup>1</sup> and this [review](https://www.sciencedirect.com/science/article/pii/S1361841524000562)<sup>2</sup>.

## Use of External Network Parameters (Fine-tuning)
Publicly available network weights are also allowed to be used. Initialization with private weights, or training on private data is not permitted in this challenge.


# Evaluation

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

### Non-Streaming

Algorithms which ingress full video sequences do not have provided reference implementations currently, but are welcomed in the challenge if they modify their API to store their hidden state, and take in the framewise inputs, similar to the above 2D streaming example.

## Prizes
Refer to synapse: https://www.synapse.org/Synapse:syn65877821/wiki/631534

# Participation

Visit our [Synapse page](https://www.synapse.org/Synapse:syn65877821/wiki/631618) to participate and obtain further details on submission.

1. Register, and email a copy of the signed registration form to challenge.stir@gmail.com
2. Test your method, or modify a provided one using [STIRMetrics](https://github.com/athaddius/STIRMetrics) on the public component of the STIR dataset.
3. Experiment with exporting an ONNX/torchscript model (if participating in the efficiency component). See [STIRHoloscan](https://github.com/athaddius/STIRHoloscan) to time your method.
4. Submit docker container for validation (instructions available on the Synapse page)
5. Submit final docker container by August 20th
6. Submit report describing your method by Late August
7. Attend MICCAI 2025 (recommended), and submit a video report explaining your method.

# Organizers

Name |  Institution
---|---
Adam Schmidt | Intuitive
Mert Karaoglu | ImFusion & TUM
Alexander Ladikos | ImFusion
Omid Mohareri | Intuitive
Simon DiMaio | Intuitive

## Sponsors

![Sponsors: ImFusion, Intuitive](/images/sponsors-25.png)

References
------
1- Schmidt, Adam, Mert Asim Karaoglu, Soham Sinha, Mingang Jang, Ho-Gun Ha, Kyungmin Jung, Kyeongmo Gu et al. "Point Tracking in Surgery--The 2024 Surgical Tattoos in Infrared (STIR) Challenge." arXiv preprint arXiv:2503.24306 (2025).

2- Schmidt, Adam, Omid Mohareri, Simon DiMaio, Michael C. Yip, and Septimiu E. Salcudean. "Tracking and mapping in medical computer vision: A review." Medical Image Analysis (2024): 103131.
