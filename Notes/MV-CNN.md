# Basic info
- Title: Multi-View Convolutional Neural Networks for 3D Shape Recognition
- Author: Hang Su, Subhransu Maji, Evangelos Kalogerakis, Erik Learned-Miller
- Affiliation: University of Massachusetts, Amherst
- Publication status: 
- Short name: MV-CNN
- Year: 2015

# Score
- Idea: 
- Usability: 
- Presentation: 
- Overall: 

# Contributions
## Problem addressed / Motivation
- Emersion of more 3D data.
- Use 2D due to its relative efficiency over 3D representations.
- No need to reduce resolution, to train in reasonable time.
- Leverage advances in image descriptors and large image databases to pre-train CNN architecture.

## Idea / Observation / Contribution
- MV-CNN related to **jittering** where transformed copies of the data are added during training to learn invariances to transformations; such as rotation or translation.
- CNN learns to combine the views instead of averaging, and can use the more informative views of the object for prediction while ignoring others.

<img src='http://vis-www.cs.umass.edu/mvcnn/images/mvcnn.png' alt="MV-CNN Network" width=600 align="middle">



## Formulation / Solver / Implementation
- All parameters of CNN are learned discriminatively to produce a single compact descriptor for 3D shape from the multiple views.
- Phong reflection model used to generate rendered views of polygon meshes, which are rendered under a perspective projection and the pixel colour is found by interpolating reflected intensity of polygon vertices.

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

