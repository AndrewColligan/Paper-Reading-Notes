# Basic info
- Title: Escape from Cells: Deep Kd-Networks for the Recognition of 3D Point Cloud Models
- Author: Roman Klokov & Victor Lempitsky
- Affiliation: Skolkovo Institute of Science and Technology
- Publication status: 
- Short name: Kd-network
- Year: 2017

# Score
- Idea: 5
- Usability: 3
- Presentation: 3
- Overall: 4

# Contributions
## Problem addressed / Motivation
- Computer graphics and computational geometry communities have used a large number of indexing structures that are far more scalable than uniform grids have been proposed, including kd-trees, octrees, binary spatial partition trees, R-trees & constructive solid geometry.
- At least some of these indexing structures are amenable for forming the base for deep architectures, in the same way as uniform grids form the base for the computations, data alignment and parameter sharing inside convolutional networks.

## Idea / Observation / Contribution
- Use kd-tree structure to form the computational graph, to share learnable parameters, and to compute a sequence of hierarchical representations in a feed-forward bottom-up fashion.
- Show that this type of deep learning method has similar accuracy results on recognition operations (classification, retrieval and part segmentation) as ConvNets.
- While having a smaller memory footprint and more efficient computations at train and test time.

<p align="center">
  <img src="https://i1.wp.com/www.itzikbs.com/wp-content/uploads/2017/09/kdnetwork.png?resize=300%2C153" width=400>
</p>

## Formulation / Solver / Implementation
- At training time, Kd-network works with point clouds of a fixed size, where point clouds of different sizes can be reduced to this size using sub or oversampling).
- A kd-tree is constructed recursively in a top-down fashion by picking the coordinate axis with the largest range (span) of point coordinates, and splitting the set of points into two equally-sized subsets, subsequently recursing to each of them.
- Once the point cloud is structured, weights are learnt for each node in the tree (which represents a subdivision along a specific axis). 
- The weights are shared for each axis across a single tree level (so all the greens in the image above have shared weights because they subdivided the data along the x dimension ). 
- They tested random and deterministic subdivisions of space and reported that the random version works best. 
- They report some drawbacks. It is sensitive to rotations (since it changes the tree structure) and to noise (if it changes the tree structure).  
- For every number of input points you either need to upsample, downsample or train a new model.

## Useful info / tips
- Kd-networks can consider and utilise properties of individual input points (such as colour, reflectivity, normal direction) if they are known.

# Evaluation
## Dataset
- MNIST
- ModelNet10
- ModelNet40
- SHREC'16
- ShapeNet

## Metrics
- Test on:
  - Shape Classification
  - Shape Retrieval
  - Part Segmentation

## Results

| Method            | ModelNet10 |          | ModelNet40 |          |
| ----------------- | ---------- | -------- | ---------- | -------- |
| Accuracy Avg      | Class      | Instance | Class      | Instance |
| Kd-Net (depth 10) | 92.8       | 93.3     | 86.3       | 90.6     |
| Kd-Net (depth 15) | 93.5       | 94.0     | 88.5       | 91.8     |

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
