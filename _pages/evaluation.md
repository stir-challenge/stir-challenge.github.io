---
layout: archive
title: "Evaluation"
permalink: /evaluation/
author_profile: true
---

The goals of the STIR challenge are:

1.   _Accuracy:_ Evaluate accuracy of tracking  and reconstruction algorithms.
2.   _Efficiency:_ Motivate efficiency of algorithms for usage in clinical applications.

These will be ranked with two different means (accuracy, and latency). Participation in (2) is optional (but highly recommended) as it comes with an additional prize, of an IGX Orin Developer Kit (see Prizes for more details). Algorithms can choose to compete in either the 2D or 3D quantification.

## Metrics

### Accuracy

We will be using $$ \delta^x_{avg} $$ (from [TAP-VID](https://tapvid.github.io/)) for ranking methods, which averages accuracy over multiple thresholds. This will be evaluated over a withheld and filtered test split for the competition. The 2D metric is averaged over accuracy thresholds of [4, 8, 16, 32, 64] pixels. The 3D metric is averaged over accuracy thresholds of [2, 4, 8, 16, 32] millimetres.


**Accuracy metrics code is available at:** [STIRMetrics](https://github.com/athaddius/STIRMetrics)

### Efficiency

Efficiency of models will be evaluated using the [NVIDIA Holoscan](https://docs.nvidia.com/holoscan/sdk-user-guide/index.html) platform, using the framework provided at [STIRHoloscan](https://github.com/athaddius/STIRHoloscan/). For participants in the efficiency challenge, we will evaluate efficiency as the combination of average framewise latency, 99%, and 95% latencies. Methods which reach an efficient threshold are viable for this prize. If your method is faster than the threshold below, you are good to go! Methods will be evaluated on an A6000 GPU. The most accurate method (according to 2D accuracy) under this threshold will receive the prize.

**Threshold:** (99 percentile + 95 percentile + average latency) / 3 < 200ms

**Note:** If fewer than 5 methods score under the latency threshold, then we will select the most accurate method from the lowest-latency 1/3 of submissions. The lowest-latency 1/3 is selected according to the same latency score. Specifics may be subject to change.

#### Tips
Evaluate your current performance using [STIRHoloscan](https://github.com/athaddius/STIRHoloscan/). Insert your model into this framework of Holoscan Operators so the organizers can time it as described on the [STIRHoloscan](https://github.com/athaddius/STIRHoloscan/) page. Ensure your model produces correct output after exporting. 


We recommend exporting PyTorch->Onnx->TensorRT to ensure efficient on-GPU performance. To participate in the efficiency segment of the challenge, start experimenting with exporting your model to onnx to enable use with Holoscan for benchmarking. [RAFT STIR](https://github.com/athaddius/RAFT_STIR) provides an example of this.

**Latency metrics code is available at:** [STIRHoloscan](https://github.com/athaddius/STIRHoloscan/)


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

Prizes in the 3D category are also valid for 2D prizes. For example, if a method is first in 3D (compared against 3D participants) and second in 2D (against 2D and 3D participants), then they will get 9 units (6 for second 2D +3 for first place in 3D) of cash. The efficiency prize will be offered to the most accurate (according to 2D accuracy) method, either 2D or 3D, that is performant above a given threshold. The exact threshold is still in deliberation, but should be set relative to the latency of the RAFT-small model. For participants looking for the efficiency prize, we recommend starting with, or comparing your method to [RAFT_STIR](https://github.com/athaddius/RAFT_STIR) in performance using [STIRHoloscan](https://github.com/athaddius/STIRHoloscan) code.

#### Cash Prizes (USD)
**2D**:
First: $2025
Second: $1350
Third: $675

**3D**:
First: $675
Second: $450
Third: $225

#### Efficiency Prize
An [IGX Orin Developer Kit](https://www.nvidia.com/en-us/edge-computing/products/igx/) equipped with the latest [RTX 6000 ADA Generation GPU](https://www.nvidia.com/en-us/design-visualization/rtx-6000/).
