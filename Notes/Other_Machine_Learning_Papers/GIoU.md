# Basic info
- Title: Generalized Intersection over Union: A Metric and A Loss for Bounding Box Regression
- Author: Hamid Rezatofighi, Nathan Tsoi, JunYoung Gwak, Amir Sadeghian, Ian Reid & Silvio Savarese
- Affiliation: Computer Science Department, Stanford University, United states & School of Computer Science, The University of Adelaide, Australia & Aibee Inc, USA
- Publication status: CVPR 2019
- Short name: GIoU
- Year: 2019

# Score
- Idea: 5
- Usability: 5
- Presentation: 5
- Overall: 5

# Contributions
## Problem addressed / Motivation
- IoU as a distance is a metric e.g. L<sub>IoU</sub> = 1 - IoU.
- IoU is also invariant to the scale of the problem.
- However, when there is not an intersect then IoU = 0 and will not reflect if the bounding boxes, it will have no gradient in these cases.

## Idea / Observation / Contribution
- A generalised IoU (GIoU) for both use as a new loss and a new metric.

<p align="center">
  <img src="https://giou.stanford.edu/_nuxt/img/3cfc41f.jpg" width=500>
</p>

## Formulation / Solver / Implementation
- Find the smallest convex shapes enclosing both the ground truth (A) and predicted (B) bounding boxes called C i.e. a large bounding box around both the bounding boxes.
- Calculate the ratio between the volume (area) occupied by C excluding A and B.
- Divide by the total volume (area) occupied by C.
- This represents a normalised measure that focuses on the empty volume (area) between A and B.
- GIoU is attained by subtracting this ratio from the IoU value.

<p align="center">
  <img src="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Imgs/GIoU.png" width=500>
</p>

## Useful info / tips
- GIoU can potentially have a steeper gradient than the IoU, therefore allowing for better optimisation.

# Evaluation
## Datasets
- PASCAL VOC
- Microsoft Common Objects in Context (MS COCO)

## Metrics
- Networks used:
  - YOLO v3
  - Faster R-CNN
  - Mack R-CNN

## Results
- Compare L<sub>GIoU</sub> to l<sub>1</sub>-smooth and L<sub>IoU</sub> as loss function.
- In each experiment, there was a relative improvement to each.

# Resource
## Paper
https://arxiv.org/abs/1902.09630

## Project page
https://giou.stanford.edu/

## Source code
https://github.com/generalized-iou

## Questions
- Can this work for the primitive 3D problem?
