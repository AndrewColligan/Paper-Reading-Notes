# Basic info
- Title: Learning localized features in 3D CAD models for manufacturability analysis of drilled holes
- Author: Sambit Ghadai, Aditya Balu, Soumik Sarkar, Adarsh Krishnamurthy
- Affiliation: Department of Mechanical Engineering, Iowa State University, IA, USA
- Publication status: 
- Short name: Learning of Hole Manufacturability

# Score
- Idea: 3
- Usability: 3
- Presentation: 3
- Overall: 3

# Contributions
## Problem addressed / Motivation
- Parts or products need to meet its specifications, while still being able to be manufactured.
- Feedback to a designer on a product's manufacturing feasibility is only given after the final design is created.
- This leads to a iterative process, leading to longer product development times and increased costs.

## Idea / Observation / Contribution
- Feature identification framework for recognising *difficult-to-manufacture* drilled holes.
- Local features of 3D voxelised CAD models are recognised using a 3D-CNN.
- Normal information of surfaces also used in addition to volume occupancy information.
- 3D-GradCAM (3D-CNN based gradient-weighted class activation mapping) is used to provide visually display the difficult-to-manufacture features outputed by the network.
- GPU-accelerated methods for converting CAD models to volume representations (voxelisation augmented with surface normals).

## Formulation / Solver / Implementation
- DLDFM (Deep Learning Design For Manufacturing) framework, used the following DFM rules to create synthetic dataset:
	1. **Depth-to-diameter ratio**: The depth-to-diamter ratio should be less than 5.0 for the machinability of the hole.
	2. **Through holes**: Since a through hole can be drilled from both directions, the depth-to-diamter ratio for a through hole should be less than 10.0 to be manufacturable.
	3. **Holes close to the edges**: A manufacturable hole should be surrounded with material of thickness at least equal to the half the diamter of the hole.
	4. **Thin sections in the depth direction of the hole**: A manufacturable hole should have material greater than half the diamter along the depth direction.
- To create voxel model, a grid of voxels in the region occupied by the object are constructed.


## Useful info / tips
- If the softmax target is very sparse and the minibatch contains only a few label classes, the gradients would be biased on these classes at each SGD iteration
- It is observed that detectors greatly affect the person search performance of baseline method and there is still a big gap between using the ground truth bounding boxes and the automatically detected ones.

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
Need to send request
https://drive.google.com/open?id=0B-GOvBat1maOVUE3WmNNUVRGamc

## Other paper reading notes

## Others

# Questions
- How to perform re-id algorithm in current framework?

# Build upon
- Performance is low on low-resolution images
- Extend to video data (plus tracking)

# Paper connections
- Faster RCNN
