---
permalink: /
title: "STIR Challenge 2025"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---
![MICCAI 2025 Logo](/images/miccai2025-logo.png)

## Description
![Header](/images/header.png)
The 2025 STIR (Surgical Tattoos in Infrared) Challenge (STIRC2025) is a challenge to quantify methods in deformable tracking, mapping and reconstruction. STIR is a part of EndoVis challenge at MICCAI 2025 (September 23-27, 2025). STIR will be quantified using a non-public test split of the publicly available STIR Dataset, STIROrig. The dataset is a stereo dataset with ground truth labels created using Infrared Tattoos<sup>1</sup>.

## Objective
Track points accurately and efficiently in videos

## Motivation
Robust tracking and mapping in deformable scenarios is essential to enable downstream tasks in medical computer vision, such as motion compensation, and subtask automation<sup>2</sup>. A robust means to evaluate these methods for clinical efficacy requires a large labelled dataset, and a standardized evaluation. The STIR challenge provides that.

Example with MFTs<sup>3</sup>
------

Here are some examples of a baseline method (MFTs) on the STIR dataset.

<video width="640" height="480" controls>
  <source src="/mft_videos/00MFT.mp4" type="video/mp4">
</video>

<video width="640" height="480" controls>
  <source src="/mft_videos/01MFT.mp4" type="video/mp4">
</video>

<video width="640" height="480" controls>
  <source src="/mft_videos/03MFT.mp4" type="video/mp4">
</video>

<video width="640" height="480" controls>
  <source src="/mft_videos/04MFT.mp4" type="video/mp4">
</video>

## News
- **Feb 4, 2025** [STIRC 2024 evaluation data](https://zenodo.org/records/14803158) shared
- **March 31, 2025** [STIRC 2024 report paper](https://arxiv.org/abs/2503.24306) shared
- **April 2, 2025** Synapse website launched
- **May 4, 2025** Webpage updated for STIRC 2025
- **May 27, 2025** Submission instructions posted


## Timeline
- **August 20, 2025** Submissions due
- **Late August, 2025** Report Submission Deadline
- **September, 23-27 2025** Challenge day at MICCAI 2025

## Organizers
*TBA*

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
## Contact
Questions about our challenge should be posted on the synapse forum for this challenge. To formally register for the challenge, please email your signed registration form to [challenge.stir@gmail.com](challenge.stir@gmail.com).

References
------
1. Schmidt, Adam, Omid Mohareri, Simon DiMaio, and Septimiu E. Salcudean. "STIR: Surgical Tattoos in Infrared." IEEE Transactions on Medical Imaging (2024).
2. Schmidt, Adam, Omid Mohareri, Simon DiMaio, Michael C. Yip, Septimiu E. Salcudean. "Tracking and mapping in medical computer vision: A review." Medical Image Analysis. 2024 Mar 2:103131.
3. Neoral, Michal, Jonáš Šerých, and Jiří Matas. "Mft: Long-term tracking of every pixel." In Proceedings of the IEEE/CVF Winter Conference on Applications of Computer Vision, pp. 6837-6847. 2024.
