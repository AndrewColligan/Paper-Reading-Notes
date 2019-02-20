# Basic info
- Title: FeatureNet: Machining feature recognition based on 3D Convolutional Neural Network
- Author: Zhibo Zhang, Prakhar Jaiswal, Rahul Rai
- Affiliation: Manufacturing and Design (MAD) Lab, Department of Mechanical and Aerospace Engineering, University of Buffalo
- Publication status: Journel of Computer-Aided Design
- Short name: FeatureNet
- Year: 2018

# Score
- Idea: 
- Usability: 
- Presentation: 
- Overall: 

# Contributions
## Problem addressed / Motivation
- Disconnect between CAD and CAM. 
- CAPP is focussed on generating a set of manufacturing operations to fabricate a given part specified by its CAD model. 
- CAPP has to interpret a given CAD model in terms of *features*, to reason about the fabrication instructions.
- Features are semantically higher level geometric elements such as hole, slot and pocket etc.

## Idea / Observation / Contribution
- Recognition of **machining features** that involve recognising different features in the CAD model of a given part.
- Use machine learning as:
	1. Inability to learn and generalise.
	2. Lack of tolerance to noise in the input CAD models.
	3. Computationally intensive and inflexible.
	4. Focused on specific types of CAD representation and thus not generalisable in cases where interoperability between different geometric representation is required.
	5. Limited in ability to handle feature variations.

## Formulation / Solver / Implementation
- Deep 3D Convolutional Neural Networks (3D-CNNs).

## Useful info / tips


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

