# Basic info
- Title: 3D-PRNN: Generating Shape Primitives with Recurrent Neural Networks
- Author: Chuhang Zou, Ersin Yumer, Jimei Yang, Duygu Ceylan, Derek Hoiem
- Affiliation: University of Illinois at Urbana-Champaign, Adobe Research
- Publication status: 
- Short name: 3D-PRNN
- Year: 2017

# Score
- Idea: 
- Usability: 
- Presentation: 
- Overall: 

# Contributions
## Problem addressed / Motivation
- Robotics and graphics application require 3D interpretations of sensory data.
- Challenge to represent 3D object geometry so that:
	1. Noisy and oartial observations can be predicted.
	2. It is useful for resoning about extent, contact and support etc.
	
![3D-PRNN](https://github.com/zouchuhang/3D-PRNN/raw/master/figs/teasor.jpg)

## Idea / Observation / Contribution
- Use of 3D primitves instead voxels as it is more **compact**.
- Primitives are also **holistic**, representing an object in few parts, which simplifies reasoning about stability, connectedness and other properties.
- Contribution is to learn 3D primitives representations of objects from unannotated 3D meshes.
- Method to fit primitves from **point clouds**.

## Formulation / Solver / Implementation
- Autoencoder architecture.
- RNN to encode an implicit shape representation and then deocde into a sequence of generated primitives to approximate the shape.
- Ground truth data acquired by method based on **Gaussian Fields** and **energy minimization** to iteratively parse shapes into primitive components.
- Optimise a differentiable loss function using robust techniques (L-BFGS).
- The network is trained jointly with a single depth image and a sequence of primitives configurations (shape, translation and rotation) that form the complete shape

## Useful info / tips
- Utilised symmetry of man-made objects to speed up primitive parsing procedure.

# Evaluation
## Dataset
- Automatically generated cubes with single hole features in each, with a label of manufacturable or non-manufacturable.
- There are two parts in the dataset: street snaps and movies.
- Low-resolution subset and occlusion subset

## Metrics
- designed different evaluation protocols by setting the gallery size to 50, 100, 500, 1, 000, 2, 000, and 4, 000
- meanAveraged Precision (mAP): A candidate window is considered as positive if its overlap with the ground truth is larger than 0.5
- top-k matching rate on bounding boxes: A matching is counted if a bounding box among the top-k predicted boxes overlaps with the ground truth larger than the threshold

## Results
- Baseline detector: ACF + Deep detector
- Baseline re-id methods: BoW with cosine distance, DenseSift+ColorHist with Euclidean and KISSME distance metric, IDNet

# Resource
## Project page
http://www.ee.cuhk.edu.hk/~xgwang/PS/dataset.html

## Source code
For the creation of voxelised GPU-accelerated models
https://github.com/idealab-isu/GPView

## Dataset


## Other paper reading notes

## Others

# Questions
- How to perform re-id algorithm in current framework?

# Build upon
- Performance is low on low-resolution images
- Extend to video data (plus tracking)

# Paper connections
- Faster RCNN

