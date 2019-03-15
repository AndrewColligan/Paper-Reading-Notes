# Basic info
- Title: Physical Primitive Decomposition
- Author: Zhijian Liu, William T. Freeman, Joshua B. Tenenbaum and Jiajun Wu
- Affiliation: Massachusetts Institute of Technology, Google Research
- Publication status: 
- Short name: PPD
- Year: 2018

# Score
- Idea: 
- Usability: 
- Presentation: 
- Overall: 

# Contributions
## Problem addressed / Motivation
- Objects are made of *functional parts*, each with distinct geometry, physics, functionality, and affordances. 
- For intelligent agents to better explore and interact with the world, there must be development of a distributed, physical, interpretable representation of objects.
- Goal is to explain the shape and physics of an object with shape primitives with physical parameters.


## Idea / Observation / Contribution
- Goal is to build a model that recovers 
- Use machine learning as:
	1. Inability to learn and generalise.
	2. Lack of tolerance to noise in the input CAD models.
	3. Computationally intensive and inflexible.
	4. Focused on specific types of CAD representation and thus not generalisable in cases where interoperability between different geometric representation is required.
	5. Limited in ability to handle feature variations.

## Formulation / Solver / Implementation
- Deep 3D Convolutional Neural Networks (3D-CNNs).

## Useful info / tips
- Large-scale shape repositiories like ShapeNet have limited annotations on object parts due to:
	1. Annotating objects and physics being labour-intensive and requiring good domain expertise.
	2. There exists intrinsic ambiguity in the ground truth: it is impossible to precisely label underlying physical object properties like densities only by images or videos.

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
http://vis-www.cs.umass.edu/mvcnn/

## Source code
https://github.com/WeiTang114/MVCNN-TensorFlow

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

