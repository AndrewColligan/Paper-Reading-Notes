# Basic info
- Title: Supervised Fitting of Geometric Primitives to 3D Point Clouds
- Author: Lingxiao Li, Minhyuk Sung, Anastasia Dubrovina, Li Yi & Leonidas Guibas
- Affiliation: Stanford University & Facebook AI Research
- Publication status: CVPR2019
- Short name: SPFN
- Year: 2019

# Score
- Idea: 5
- Usability: 4
- Presentation: 5
- Overall: 4

# Contributions
## Problem addressed / Motivation
- Most of the previous primitive work has been aimed at solving *perceptual* learning tasks including: parsing shapes, or generating a rough abstraction of the geometry with bounding primitives.
- Their goal is to precisely fit geometric primitives to **shape surface**, even with the presence of noise in the input.
- RANSAC-based methods (random sample consensus) remains the standard, but suffer from a difficulty of finding suitable algorithm parameters.
- This prevents RANSAC methods from scaling up to a large number of categories of diverse shapes.

## Idea / Observation / Contribution
- Proposed network takes point clouds as input and predicts a varying number of primitives of different types with accurate parameters.
- Does not directly output primitive parameters, but instead predicts three kind of per-point properties: point-to-primitive membership, surface normal, and the type of primitive the point belongs to.
- Per-point properties, means primitive parameters are computed in an algebraic way, making the fitting loss fully backpropable.

<p align="center">
  <img src="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Imgs/SPFN_1.png" width=400>
</p>

## Formulation / Solver / Implementation
- Supervised approach.
- PointNet++ takes input point cloud and outputs three per-point properties: point-to-primitive membership, normals and associated primitive type.
- Three separate fully-connected layers are added to the end of PointNet++ in order to predict the per-point properties.
- The order of ground truth primitives are matched with the output in the primitive reordering step.
- A *Relaxed Intersection over Union* (RIoU) is used for all pairs of the columns from the membership matirces W and &Wcirc;. The *Hungarian matching* is used to determine the best one-to-one correspondence for the primitive reordering step.
- Then, the output primitive parameters are estimated from the point properties in the model estimations step.
- The loss is defined as the sum of five loss terms (segmentation loss, point normal angle loss, per-point primitive type loss, fitting residual loss and axis angle loss).

<p align="center">
  <img src="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Imgs/SPFN_2.png" width=800>
</p>

# Evaluation
## Dataset
- ANSI 3D mechanical component models with 17k CAD models.

## Metrics
- Primitives types: plane, sphere, cylinder and cones.
- Max number of primitives = 20.
- K<sub>max</sub> set to 24 to allow the neural net to assign a small number of points to the extra columns, effectively marking those points unassigned.
- Evaluation metrics include:
  - Segmentation Mean IoU
  - Mean primitive type accuracy
  - Mean point normal difference
  - Mean primitive axis difference
  - Mean/std. {S<sub>k</sub>} residual
  - {S<sub>k</sub>} coverage
  - P coverage

## Results
| Method | Seg (Mean IoU) | Primitive Type | Point Normal | Primitive Axis | {S<sub>k</sub>} Residual Mean &plusmn; Std. |
| ------ | -------------- | -------------- | ------------ | -------------- | -------------------------                   |
| RANSAC | 60.56          | 93.13          | 8.15         | 7.02           | 0.054 &plusmn; 0.307                        |
| SPFN   | 77.14          | 96.93          | 8.66         | 1.51           | 0.011 &plusmn; 0.131                        |
# Resource
## Paper
https://arxiv.org/abs/1811.08988

## Source code
https://github.com/csimstu2/SPFN
