# Basic info
- Title: Supervised Fitting of Geometric Primitives to 3D Point Clouds
- Author: Lingxiao Li, Minhyuk Sung, Anastasia Dubrovina, Li Yi & Leonidas Guibas
- Affiliation: Stanford University & Facebook AI Research
- Publication status: CVPR2019
- Short name: SPFN
- Year: 2019

# Score
- Idea: 
- Usability: 
- Presentation: 
- Overall: 

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
- The order of ground truth primitives are matched with the output in the primitive reordering step.
- Then, the output primitive parameters are estimated from the point properties in the model estimations step.
- The loss is defined as the sum of five loss terms.

<p align="center">
  <img src="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Imgs/SPFN_2.png" width=800>
</p>

## Useful info / tips



# Evaluation
## Dataset
- ANSI 3D mechanical component models with 17k CAD models.

## Metrics
- Primitives types: plane, sphere, cylinder and cones.

## Results


# Resource
## Paper


## Project page


## Source code


## Dataset


## Other paper reading notes


## Others


## Questions


## Build upon


## Paper connections


## Software & Hardware

