---
layout: archive
title: "Participation"
permalink: /participation/
author_profile: true
---

## Development and Submission
Here is a step-by-step guide on how to participate in the challenge:
1. Clone the [stir-challenge-2026-inference](https://github.com/mertkaraoglu/stir-challenge-2026-inference) repository.
2. Follow our guideline outlined in the repo's readme to integrate and package your model inside a Docker image.
3. Test your model qualitatively using our provided validation sequences.
4. Upload your Docker image to any file-sharing service (e.g., Google Drive, Synapse, etc.) and share the link with us in the submission email following the instructions below.

### Important Rules for Submission
Do not modify any existing dataset or inference pipeline files in the inference repository.
Your model must be contained in a single file, following the format of the existing sample models.
You are allowed and encouraged to modify the `pyproject.toml` file to add dependencies.
Any changes to the core files of the framework may result in rejection of your submission.

### Evaluation Framework
We will use [stir-challenge-2026-metrics](https://github.com/mertkaraoglu/stir-challenge-2026-metrics) to access your model's outputs and benchmark its performance.

### Using Previous Year's Data and Framework for Validation
You are more than welcome to use the previous years' data and framework ([STIRC 2024](/stirc-2024/), [STIRC 2025](/stirc-2025/)) for validation purposes.
Please note that you will need to follow the corresponding guidelines and adapt your model to the old framework as well.

***vRAM Constraints:** The evaluations will be performed on a single, independent, workstation equipped with an RTX6000 Ada GPU (48GB vRAM). The longest of our sequences is 30 seconds. Please consider this when developing your model.*

### Email Template
**Visit our [Synapse page](https://www.synapse.org/Synapse:syn65877821/wiki/631618) to participate and obtain further details on submission.**
Email `challenge.stir@gmail.com` with a link to download your container. Attach the signed form EndoVis Participant Form if you have not already done so. Teams are limited to one submission per component. A video and report will be due. (see How To Participate for instructions)

```markdown
**Subject line**

STIR Submission <teamname> <submissiontype>

**Body**

Team Name:
Team Members:
Team Contact Email:
Link to Docker image and rundocker.sh for submission: (for each submission)
Type of Submission: (Any of: 2D, 3D, 2D+latency/3D+latency)
```

#### Questions
Please direct your questions to the synapse forum if they can be relevant to other participants, or challenge.stir@gmail.com if not.
