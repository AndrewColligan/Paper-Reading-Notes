# Basic info
- Title: PointGrid: A Deep Network for 3D Shape Understanding
- Author: Truc Le and Ye Duan
- Affiliation: Univeristy of Missouri - Columbia
- Publication status:  2018 IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)
- Short name: PointGrid
- Year: 2018

# Score
- Idea: 
- Usability: 
- Presentation: 
- Overall: 

# Contributions
## Problem addressed / Motivation
- Voxels and distance fields are computationally inefficient for representing finer geometry details due to requiring a very high resolution grid.

## Idea / Observation / Contribution
- A 3D convolutional network that incorporates a constant number of points within each grid cell thus allowing the nwtowrk to learn higher order local approximation functions
- Compared to PointNet that can consume unorganised poitnsets in 3D, in PointGrid, all 3D points share the same set of multi-layer perceptrons, which independently transform individual points.
- However, a single max-pooling layer is the only global operation in PointNet, which limites its ability to examine contextual neighbourhood structure of the points.

## Formulation / Solver / Implementation


## Useful info / tips


# Evaluation
## Dataset


## Metrics


## Results


# Resource
## Paper


## Source code
https://github.com/trucleduc/PointGrid

## Dataset


## Other paper reading notes

## Others

## Questions


## Build upon


## Paper connections


## Software
- Tensorflow

