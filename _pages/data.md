---
layout: archive
title: "Data"
permalink: /data/
author_profile: true
---
![](/images/STIR_summary.png)
The STIR dataset includes many sequences (over 4 hours) of tissue deformation, and the publicly released version can be used for both training and validation.

## Data Description

The test dataset contains around 60 sequences, with a total of 14k frames. No sequences are longer than 4 minutes in length.

## Use of External Data
Public, available data are usable for training. Usable datasets with deformation or tracking labels are mentioned in [this](https://www.sciencedirect.com/science/article/pii/S1361841524000562)<sup>1</sup> review. Additional datasets include publicly available datasets without deformation labels that can be used in an unsupervised manner, such as [StereoMIS](https://zenodo.org/records/7727692)<sup>2</sup>. Publicly available network weights are also allowed. Initialization with private weights, or training on private data is not permitted in this challenge.

References
------
1- Schmidt, Adam, Omid Mohareri, Simon DiMaio, Michael C. Yip, and Septimiu E. Salcudean. "Tracking and mapping in medical computer vision: A review." Medical Image Analysis (2024): 103131.

2- Hayoz, Michel, Christopher Hahne, Mathias Gallardo, Daniel Candinas, Thomas Kurmann, Maximilian Allan, and Raphael Sznitman. "Learning how to robustly estimate camera pose in endoscopic videos." International journal of computer assisted radiology and surgery 18, no. 7 (2023): 1185-1192.
