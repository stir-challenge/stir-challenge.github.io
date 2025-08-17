---
layout: archive
title: "Data"
permalink: /data/
author_profile: true
---
![](/images/STIR_summary.png)
The STIR dataset (STIROrig) includes many sequences (over 4 hours) of tissue deformation, and the [publicly](https://arxiv.org/abs/2309.16782) released version can be used for both training and validation. The 2024 challenge (STIRC2024) [data](https://zenodo.org/records/14803158) provides a more filtered and orthogonal dataset that can be used for validation of algorithms. An similarly distributed non-intersecting dataset (STIRC2025) will be used for the 2025 challenge evaluation.

## STIRC2025 Test and Validation Data
The test dataset for STIRC2025 will be the data we use for this challenge. It has no intersection with any of the other released datasets. STIRC2025 contains around 32 sequences. Use prior challenge data (STIRC2024) to validate your methods.

## Use of External Data
Publicly available data are usable for training. Recommended datasets with deformation or tracking labels are mentioned in the prior years challenge [paper](https://arxiv.org/abs/2503.24306)<sup>1</sup> and this [review](https://www.sciencedirect.com/science/article/pii/S1361841524000562)<sup>2</sup>.

## Use of External Network Parameters (Fine-tuning)
Publicly available network weights are also allowed to be used. Initialization with private weights, or training on private data is not permitted in this challenge.

References
------
1- Schmidt, Adam, Mert Asim Karaoglu, Soham Sinha, Mingang Jang, Ho-Gun Ha, Kyungmin Jung, Kyeongmo Gu et al. "Point Tracking in Surgery--The 2024 Surgical Tattoos in Infrared (STIR) Challenge." arXiv preprint arXiv:2503.24306 (2025).
2- Schmidt, Adam, Omid Mohareri, ddSimon DiMaio, Michael C. Yip, and Septimiu E. Salcudean. "Tracking and mapping in medical computer vision: A review." Medical Image Analysis (2024): 103131.
