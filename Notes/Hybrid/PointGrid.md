# Basic info
- Title: PointGrid: A Deep Network for 3D Shape Understanding
- Author: Truc Le and Ye Duan
- Affiliation: Univeristy of Missouri - Columbia
- Publication status:  2018 IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)
- Short name: PointGrid
- Year: 2018

# Score
- Idea: 4
- Usability: 4
- Presentation: 4
- Overall: 4

# Contributions
## Problem addressed / Motivation
- Voxels and distance fields are computationally inefficient for representing finer geometry details due to requiring a very high resolution grid.
<p align="center">
  <img src="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Imgs/pointgrid.png" width = 500>
</p>
## Idea / Observation / Contribution
- Hybrid of point cloud and grid techniques, that scales better than volumetric grid and avoid information loss at the same time.
- A 3D convolutional network that incorporates a constant number of points within each grid cell thus allowing the network to learn higher order local approximation functions.
- Compared to PointNet that can consume unorganised pointsets in 3D, in PointGrid, all 3D points share the same set of multi-layer perceptrons, which independently transform individual points.
- However, a single max-pooling layer is the only global operation in PointNet, which limits its ability to examine contextual neighbourhood structure of the points.

## Formulation / Solver / Implementation
- Has an embedding volumetric grid that has the regular structure, which allows 3D convolutions to extract global information hierarchically.
- In each grid cell, a constant number of points (e.g. *K*) are sampled to overcome the grid size limitation.
- The sampling points within the grid cell can better represent the local geometry shape details while the grid scales well with respect to data size as it only scales linearly in *K*, not cubicly as in pure volumetric grid.
- Stack points' coordinates as features for each cell. As a result, a cell with K points will have features 3K for corresponding *x*, *y* and *z* coordinates.
- Point quantisation used for sampling.
- Classification and segmentation were performed.

<p align="center">
  <img src="https://github.com/timzhang642/3D-Machine-Learning/blob/master/imgs/PointGrid-%20A%20Deep%20Network%20for%203D%20Shape%20Understanding%20(2018).jpeg?raw=true" width = 500>
</p>

# Evaluation
## Dataset
- ModelNet40
- ShapeNet-Core55

## Metrics
- 16<sup>3</sup> grid.
- Randomly rotate the point cloud objects along the up-axis and jittering the position of each point by a Gaussian noise with zero mean and 0.02 standard deviation.

## Results
- ModelNet40 accuracy: 92.0%.
- ShapeNet-Core55: 86.1%.
- ShapeNet Segmentation: 86.4%.

# Resource
## Paper
http://openaccess.thecvf.com/content_cvpr_2018/papers/Le_PointGrid_A_Deep_CVPR_2018_paper.pdf

## Source code
https://github.com/trucleduc/PointGrid

## Questions
- Can CSGNet primitives be fitted onto the grid?

## Build upon
- Explore other advanced sampling techniques other than *point quantisation* like furthest dampling which may provide better representation of the local shape.

## Paper connections
- Point cloud
- Grid

## Software & Hardware
- Tensorflow
- Nvidia Titan X

