# Basic info
- Title: Escape from Cells: Deep Kd-Networks for the Recognition of 3D Point Cloud Models
- Author: Roman Klokov & Victor Lempitsky
- Affiliation: Skolkovo Institute of Science and Technology
- Publication status: 
- Short name: Kd-network
- Year: 2017

# Score
- Idea: 
- Usability: 
- Presentation: 
- Overall: 

# Contributions
## Problem addressed / Motivation
- Computer graphics and computational geometry communities have used a large number of indexing structures that are far more scalable than uniform grids have been proposed, including kd-trees, octrees, binary spatial partition trees, R-trees & constructive solid geometry.
- Whether at least some of these indexing structures are amenable for forming the base for deep architectures, in the same way as uniform grids form the base for the computations, data alignment and parameter sharing inside convolutional networks.

## Idea / Observation / Contribution
- Use kd-tree structure to form the computational graph, to share learnable parameters, and to compute a sequence of hierarchical representations in a feed-forward bottom-up fashion.

## Formulation / Solver / Implementation


## Useful info / tips


# Evaluation
## Dataset
- MNIST
- ModelNet10
- ModelNet40
- SHREC'16
- ShapeNet

## Metrics


## Results


# Resource
## Paper
https://arxiv.org/abs/1704.01222

## Source code
https://github.com/fxia22/kdnet.pytorch

## Questions


## Build upon


## Paper connections
- Kd-trees

## Software & Hardware
- Pytorch
- Theano
- Lasagne
- NVidia Titan X (6 days of training)
- Trained 16 hours on depth-10 model
- NVidia Titan Black (depth-15 model trained in 5 days)
