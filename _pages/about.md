---
permalink: /
title: "STIR Challenge 2026"
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

![MICCAI 2026 Logo](/images/miccai2026-logo.png)

## Description

<!--![Header](/images/header.png)-->

The 2026 STIR (Surgical Tattoos in Infrared) Challenge (STIRC2026) is a challenge to quantify methods in deformable tracking, mapping and reconstruction. STIR is a part of EndoVis challenge at MICCAI 2026. STIR will be quantified using a non-public test split of the publicly available STIR Dataset, STIROrig. The dataset is a stereo dataset with ground truth labels created using Infrared Tattoos<sup>1</sup>.

## Objective

Track points accurately and efficiently in videos.

## Motivation

Robust tracking and mapping in deformable scenarios is essential to enable downstream tasks in medical computer vision, such as motion compensation, and subtask automation<sup>2</sup>. A robust means to evaluate these methods for clinical efficacy requires a large labelled dataset, and a standardized evaluation. The STIR challenge provides that.

## Example with MFTs<sup>3</sup>

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

- **May 21, 2026** Webpage updated for STIRC 2026

## Timeline
![STIR 2026 Timeline](/images/stir-2026-timeline.svg)
- **May 30, 2026** Open for submissions
- **September 04, 2026** Submissions deadline
- **September 06, 2026** Submission reports deadline
- **September 27 - October 01, 2026** Challenge day at MICCAI 2026

## Organizers

| Name              | Institution    |
| ----------------- | -------------- |
| Adam Schmidt      | Intuitive      |
| Mert Karaoglu     | ImFusion & TUM |
| Alexander Ladikos | ImFusion       |
| Omid Mohareri     | Intuitive      |

## Sponsors

![Sponsors: ImFusion, Intuitive](/images/sponsors-25.png)

## Contact

Questions about our challenge should be posted on the [synapse forum](https://www.synapse.org/Synapse:syn74381557/wiki/640004) for this challenge, additional details may be found there. To formally register for the challenge, please email your signed registration form to [challenge.stir@gmail.com](challenge.stir@gmail.com).

## References

1. Schmidt, Adam, Omid Mohareri, Simon DiMaio, and Septimiu E. Salcudean. "STIR: Surgical Tattoos in Infrared." IEEE Transactions on Medical Imaging (2024).
2. Schmidt, Adam, Omid Mohareri, Simon DiMaio, Michael C. Yip, Septimiu E. Salcudean. "Tracking and mapping in medical computer vision: A review." Medical Image Analysis. 2024 Mar 2:103131.
3. Neoral, Michal, Jonáš Šerých, and Jiří Matas. "Mft: Long-term tracking of every pixel." In Proceedings of the IEEE/CVF Winter Conference on Applications of Computer Vision, pp. 6837-6847. 2024.
