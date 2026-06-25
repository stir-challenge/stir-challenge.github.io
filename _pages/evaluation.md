---
layout: archive
title: "Evaluation"
permalink: /evaluation/
author_profile: true
---

The goals of the STIR Challenge 2026 are:

1. _Accuracy:_ Evaluate accuracy of tracking and reconstruction algorithms.
2. _Efficiency:_ Motivate efficiency of algorithms for usage in clinical applications.

These will be ranked with two different means (accuracy and latency). Participation in (2) is optional (but highly recommended) as it comes with an additional prize. Algorithms can choose to compete in either the 2D (mono) or 3D (stereo) track.

## New for 2026: Temporally Denser Annotations

In previous years, tracking was evaluated only at the start and end points defined by infrared tattoos, reducing accuracy assessment to endpoint error. This year's annotations are **temporally denser** — each annotated frame carries per-point 2D coordinates in both left and right images as well as per-point **visibility (occlusion) labels**. This enables full Jaccard-based evaluation and explicit occlusion scoring.

## Metrics
*For more details, see the [STIR Metrics](https://github.com/mertkaraoglu/stir-challenge-2026-metrics/) repository.*

### Important Notes on Stereo Data
- **Visibility** For the stereo case, the visibility is defined as the visibility of a point together on both left and right images. It is defined to `true` only when the point is visible on both images.
- **Queries** Stereo queries are only initialized on the left image, meaning that even for the first frame, the method must predict the position of the point on the right image (i.e. the disparity).

### Accuracy

Three metrics are reported, all averaged over thresholds $$ \tau \in \{2, 4, 8, 16, 32\} $$ pixels (2D) or mm (3D).

#### Average Jaccard (AJ) — Primary Ranking Metric

Average Jaccard (AJ) is chosen as the primary metric as it combines the occlusion accuracy (OA) and tracking accuracy (ATA) in a single metric.
For each threshold $$ \tau $$, every tracked point at every frame is counted as one of three cases:

- **True Positive (TP):** the method predicts the point as visible, the ground truth also marks it visible, and the predicted location is within $$ \tau $$ of the ground-truth location.
- **False Positive (FP):** the method predicts the point as visible, but either the ground truth marks it occluded, or the location error exceeds $$ \tau $$.
- **False Negative (FN):** the ground truth marks the point as visible, but either the method predicts it occluded, or the location error exceeds $$ \tau $$.

$$
\text{AJ}_\tau = \frac{\text{TP}_\tau}{\text{TP}_\tau + \text{FP}_\tau + \text{FN}_\tau}
$$

The overall score is the mean across thresholds:

$$
\text{AJ}_{avg} = \frac{1}{5} \sum_{\tau} \text{AJ}_\tau
$$

#### Average Tracking Accuracy (ATA) — Supplementary Metric

ATA measures localisation accuracy restricted to ground-truth visible frames, without penalising false-positive visibility predictions. For each threshold $$ \tau $$, it counts the fraction of ground-truth-visible points whose predicted location falls within $$ \tau $$, regardless of the predicted visibility label:

$$
\text{ATA}_\tau = \frac{\text{# visible ground-truth points predicted within } \tau}{\text{# visible ground-truth points}}
\qquad
\text{ATA}_{avg} = \frac{1}{5} \sum_{\tau} \text{ATA}_\tau
$$

#### Occlusion Accuracy (OA) — Supplementary Metric

The fraction of all point-frames where the predicted visibility label (visible / occluded) matches the ground-truth label:

$$
\text{OA} = \frac{\text{# points with correct visibility prediction}}{\text{# total points}}
$$

**Accuracy metrics code is available at:** [STIRMetrics](https://github.com/mertkaraoglu/stir-challenge-2026-metrics)

### Efficiency

The latency metric is the **95th-percentile of per-frame processing latencies** (p95, in ms) across all test sequences, excluding warm-up frames. To qualify for the efficiency prize, a method must:

- Achieve **at least 90 % of the highest 2D AJ score** among all submitted methods, and
- Have the **lowest p95 latency** among those qualifying methods.

## Algorithm Specification
In this year's challenge, each video is streamed frame-by-frame.
Targeting online (streaming) use cases, the model predictions are also cached immediately after each process call.

*For more details and examples, see the [STIR Inference](https://github.com/mertkaraoglu/stir-challenge-2026-inference/) repository. You are allowed to add your model inside the [models folder](https://github.com/mertkaraoglu/stir-challenge-2026-inference/tree/main/models) and can not make changes in the [mono](https://github.com/mertkaraoglu/stir-challenge-2026-inference/blob/main/mono.py) or [stereo](https://github.com/mertkaraoglu/stir-challenge-2026-inference/blob/main/stereo.py) inference scripts.*

## Prizes

Refer to [synapse](https://www.synapse.org/Synapse:syn74381557/wiki/)
