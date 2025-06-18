---
layout: archive
title: "Participation"
permalink: /participation/
author_profile: true
---
## Getting Started
Visit our [Synapse page](https://www.synapse.org/Synapse:syn65877821/wiki/631618) to participate and obtain further details on submission.

### Export Docker Image
We recommend starting with the docker container at STIRMetrics
After you have finished setting up your model within docker, get your container ID:
```bash
docker ps
```
After which, run:
```bash
docker commit <container_id> <team_name>
```
This will commit your docker container to an image file which the challenge organizers can then use. Upload this docker image to a file-sharing website of your choice. Modify the commented 'FOR SUBMISSION' piece of rundocker.sh to include a run command, and submit your version of this script alongside your container image. Organizers will use this to run your docker image as a standalone method. Your method paired with the rundocker.sh must run all necessary commands and then exit; the organizers should not need to enter your container. Please make sure to submit your method early for validation so that we can ensure it runs.

### Email Template
Email `challenge.stir@gmail.com` with a link to download your container. Attach the signed form EndoVis Participant Form if you have not already done so. Teams are limited to one submission per component. A video and report will be due September 30th. (see How To Participate for instructions)

**Subject line**

STIR Submission <teamname> <submissiontype>

**Body**

Team Name:
Team Members:
Team Contact Email:
Link to Docker image and rundocker.sh for submission: (for each submission)
Type of Submission: (Any of: 2D, 3D, 2D+latency/3D+latency)

### Accuracy Component

#### 2D
Use the code at STIRMetrics to design your model, such that your model outputs point locations to the output directory. The challenge organizers will enter your docker container and run:
```bash
python datatest/flow2d.py --num_data -1 --showvis 0 --jsonsuffix test --modeltype <YOURMODEL> --ontestingset 1
```
Ensure that this command works (you can set num_data to something small (eg. 3) to verify this runs). This will output the locations at the end of each video clip to the output directory `/workspace/output`.
**Note:** When submitting your method along with rundocker.sh, make sure your code runs the above command.

#### 3D
Use the code at STIRMetrics to design your model, such that your model outputs point locations in the full-scale image and 3D to the output directory. The challenge organizers will enter your docker container and run:
```bash
python datatest/flow3d.py --num_data -1 --showvis 0 --jsonsuffix test --modeltype <YOURMODEL> --ontestingset 1
```
Ensure that this command works (you can set num_data something small (eg. 3) to verify this runs). This will output the locations at the end of each video clip to the output directory `/workspace/output`.
**Note:** When submitting your method along with rundocker.sh, make sure your code runs the above command.

#### Latency
First, ensure your model works for the accuracy component that your team is participating in (2D or 3D, as detailed above). Then, make sure that your model latency is logged (ie. keep it wrapped in `LogLatency` in flow2d.py or flow3d.py).

#### Questions
Please direct your questions to the synapse forum if they can be relevant to other participants, or challenge.stir@gmail.com if not.
