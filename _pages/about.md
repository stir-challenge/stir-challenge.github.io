---
permalink: /
title: "STIR Challenge 2024"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

## Description
The STIR Challenge is designed to quantify methods in deformable tracking, mapping and reconstruction. STIR is a part of EndoVis challenge at MICCAI 2024 (October 6-10, 2024). STIR will be quantified using a non-public test split of the publicly available STIR Dataset. The dataset is a stereo dataset with ground truth labels created using Infrared Tattoos<sup>1</sup>

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

## Timeline

- **April 3** Challenge launch, 2D Evaluation Release
- **Mid-June** 3D Quantification Release
- **October 6-10**  MICCAI 2024


## Sponsors

![Sponsors: NVIDIA, ImFusion, Intuitive](/images/sponsors.png)


## Organizers

Name |  Institution
---|---
Adam Schmidt | Intuitive & UBC
Mert Karaoglu | ImFusion & TUM
Soham Sinha | NVIDIA
Alexander Ladikos | ImFusion
Omid Mohareri | Intuitive
Simon DiMaio | Intuitive
Tim Salcudean | UBC

## Contact

Quick questions about our challenge can be posed via email or slack (recommended). Email adamschmidt@ece.ubc.ca to be added, or register for the challenge above, and be added via your email address.

References
------
1- Schmidt, Adam, Omid Mohareri, Simon DiMaio, and Septimiu E. Salcudean. "STIR: Surgical Tattoos in Infrared." IEEE Transactions on Medical Imaging (2024).
2- Schmidt, Adam, Omid Mohareri, Simon DiMaio, Michael C. Yip, Septimiu E. Salcudean. "Tracking and mapping in medical computer vision: A review." Medical Image Analysis. 2024 Mar 2:103131.
3- Neoral, Michal, Jonáš Šerých, and Jiří Matas. "Mft: Long-term tracking of every pixel." In Proceedings of the IEEE/CVF Winter Conference on Applications of Computer Vision, pp. 6837-6847. 2024.
