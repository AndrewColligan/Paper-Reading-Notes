# Basic info
- Title: FusionNet: 3D Object Classification Using Multiple Data Representation
- Author: Vishakh Hegde, Reza Zadeh
- Affiliation: Matroid Inc. and Standford University
- Publication status: 
- Short name: FusionNet

# Score
- Idea: 3
- Usability: 4
- Presentation: 3
- Overall: 3

# Contributions
## Problem addressed / Motivation
- High-quality 3D object recognition is important for the future of vision and robotic systems.
- The amount of 3D content creation publicily available is rapidly increasing.
- As it is used for augmented reality and self driving cars.

## Idea / Observation / Contribution
- Combine volumetric voxel representation and 2D multi-view representation for training relatively weak classifiers.
- Introduce two new CNNs for volumetric data, with one having significantly less number of parameters compared to standard CNNs used on 2D RGB images such as AlexNet.
- One of the networks uses an inception module used in GoogLeNet.
- This utilises transfer learning from pre-trained network on large ImageNet dataset for the multi-view representation and uses the volumetric information.

## Formulation / Solver / Implementation
- 


## Useful info / tips
- If the softmax target is very sparse and the minibatch contains only a few label classes, the gradients would be biased on these classes at each SGD iteration
- It is observed that detectors greatly affect the person search performance of baseline method and there is still a big gap between using the ground truth bounding boxes and the automatically detected ones.

# Evaluation
## Dataset
- 3D model classification has been limited due to unavailability of large scale training sets like ImageNet.


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

