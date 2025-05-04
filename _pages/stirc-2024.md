---
layout: archive
title: "STIRC 2024"
permalink: /stirc-2024/
author_profile: true
---
![Holoscan platform](/images/miccai2024-logo.png)

# [📄 Report Paper](https://arxiv.org/abs/2503.24306) 

# Timeline

- **April 3, 2024** Challenge launch, 2D Evaluation Release
- **Mid-June, 2024** 3D Quantification Release
- **October 6-10, 2024**  MICCAI 2024
- **Early August, 2024** Docker Instructions Available
- **September 23, 2024** Docker Container Submission Deadline
- **September 30, 2024** Report Submission Deadline
- **October 6-10, 2024** MICCAI 2024, challenge results

# Dataset

The test dataset contains around 60 sequences, with a total of 14k frames. No sequences are longer than 4 minutes in length.

*The evaluation set (STIRC2024) can be found [**here**](https://zenodo.org/records/14803158).*

## Use of External Data
Public, available data are usable for training. Usable datasets with deformation or tracking labels are mentioned in [this](https://www.sciencedirect.com/science/article/pii/S1361841524000562)<sup>1</sup> review. Additional datasets include publicly available datasets without deformation labels that can be used in an unsupervised manner, such as [StereoMIS](https://zenodo.org/records/7727692)<sup>2</sup>. Publicly available network weights are also allowed. Initialization with private weights, or training on private data is not permitted in this challenge.


# Evaluation
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

# Participation

Visit our [Synapse page](https://www.synapse.org/#!Synapse:syn54126082/wiki/626617) to participate and obtain further details on submission.


1. Register, and email a copy of the signed registration form to adam.schmidt@intusurg.com
2. Test your method, or modify a provided one using [STIRMetrics](https://github.com/athaddius/STIRMetrics) on the public component of the STIR dataset.
3. Experiment with exporting an ONNX/torchscript model (if participating in the efficiency component). See [RAFT_STIR](https://github.com/athaddius/RAFT_STIR) for reference, and [STIRHoloscan](https://github.com/athaddius/STIRHoloscan) to time your method.
4. Submit docker container for validation (instructions are available on the [Synapse page](https://www.synapse.org/#!Synapse:syn54126082/wiki/626617))
5. Submit final docker container by September 23rd
6. Submit report describing your method by September 30th
7. Attend MICCAI 2024 (recommended), and submit a video report explaining your method.

# Organizers

Name |  Institution
---|---
Adam Schmidt | Intuitive & UBC
Mert Karaoglu | ImFusion & TUM
Soham Sinha | NVIDIA
Alexander Ladikos | ImFusion
Omid Mohareri | Intuitive
Simon DiMaio | Intuitive
Tim Salcudean | UBC

## Sponsors

![Sponsors: NVIDIA, ImFusion, Intuitive](/images/sponsors.png)

References
------
1- Schmidt, Adam, Omid Mohareri, Simon DiMaio, Michael C. Yip, and Septimiu E. Salcudean. "Tracking and mapping in medical computer vision: A review." Medical Image Analysis (2024): 103131.

2- Hayoz, Michel, Christopher Hahne, Mathias Gallardo, Daniel Candinas, Thomas Kurmann, Maximilian Allan, and Raphael Sznitman. "Learning how to robustly estimate camera pose in endoscopic videos." International journal of computer assisted radiology and surgery 18, no. 7 (2023): 1185-1192.
