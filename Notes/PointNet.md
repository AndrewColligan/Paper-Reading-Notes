# Basic info
- Title: PointNet: Deep Learning on Point Sets for 3D Classification and Segmentation
- Author: Charles R. Qi, Hao Su, Kaichun Mo, Leonidas J. Guibas
- Affiliation: Stanford University
- Publication status: 2017 IEEE Conference on Computer Vision and Pattern Recognition
- Short name: PointNet
- Year: 2017

# Score
- Idea: 
- Usability: 
- Presentation: 
- Overall: 

# Contributions
## Problem addressed / Motivation
- Input data formats for NN architectures are regular.
- Point clouds or meshes are not regular format, therefore are normally converted in different representation.
- This makes data unnecessarily voluminous, which introduces quantisation artifacts that obscure natural invariances of data.

## Idea / Observation / Contribution
- Network that directly takes point clouds as input and outputs either class labels for entire input or per point segment/part labels for each point of the input.
- Network learns a set of optimisation functions that select interesting or informative points of the point cloud and encode the reason for their selection.


## Formulation / Solver / Implementation
- As point cloud is just a set of points and therefore invariant to permutations of its members, necessitating certain symmetrisations in the net computation.
- Invariances to rigid motions need to be considered.

## Useful info / tips
- Point clouds are simple and unified structures that avoid the combinatorial irregularities and complexities of meshes, and thus are easier to learn.

# Evaluation
## Dataset


## Metrics


## Results


# Resource
## Project page


## Source code


## Dataset


## Other paper reading notes

## Others

# Questions

# Build upon

# Paper connections

# Key Words

# Equipment & Software
