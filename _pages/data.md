---
layout: archive
title: "Data"
permalink: /data/
author_profile: true
---
![](/images/STIR_summary.png)
The STIR dataset (STIROrig) includes many sequences (over 4 hours) of tissue deformation, and the [publicly](https://arxiv.org/abs/2309.16782) released version can be used for both training and validation.
Originally, the dataset is annotated with infrared visible tattoos allowing to locate landmarks on the tissue surface on start and end frames of sequences.

## Previous Years' Data and Annotations
The challenges in [2024](https://zenodo.org/records/14803158) and 2025 contained a filtered and orthogonal dataset using the same structure of annotations.

## New for 2026: Temporally Denser Evaluation
This year, we introduce manually annotated, temporally denser tracking and visibility labels. These annotations enable a more accurate evaluation of tracking performance and offer deeper insights into the challenges posed by the coupled scene and camera motion.

The benchmark comprises around 10 sequences ranging from 5 to 30 seconds in duration, captured at 25 Hz. Each tracking point is initialized in the very first frame, with position and visibility labels provided at a frequency of 1 Hz.

## Use of External Data
Publicly available data are usable for training. Recommended datasets with deformation or tracking labels are mentioned in the prior years challenge [paper](https://arxiv.org/abs/2503.24306)<sup>1</sup> and this [review](https://www.sciencedirect.com/science/article/pii/S1361841524000562)<sup>2</sup>.

## Use of External Network Parameters (Fine-tuning)
Publicly available network weights are also allowed to be used. Initialization with private weights, or training on private data is not permitted in this challenge.

References
------
1- Schmidt, Adam, Mert Asim Karaoglu, Soham Sinha, Mingang Jang, Ho-Gun Ha, Kyungmin Jung, Kyeongmo Gu et al. "Point Tracking in Surgery--The 2024 Surgical Tattoos in Infrared (STIR) Challenge." arXiv preprint arXiv:2503.24306 (2025).

2- Schmidt, Adam, Omid Mohareri, ddSimon DiMaio, Michael C. Yip, and Septimiu E. Salcudean. "Tracking and mapping in medical computer vision: A review." Medical Image Analysis (2024): 103131.
