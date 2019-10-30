# Basic info
- Title: PointConv: Deep Convolutional Networks on 3D Point Clouds
- Author: Wenxuan Wu, Zhongang Qi & Li Fuxin
- Affiliation: CORIS Institute, Oregon State University
- Publication status: 2019 CVPR
- Short name: PointConv

# Score
- Idea: 
- Usability: 
- Presentation: 
- Overall: 

# Contributions
## Problem addressed / Motivation


## Idea / Observation / Contribution
- An approach to perform convolution on 3D point clouds with non-uniform sampling.
- Propose an **inverse-density scale** to re-weight the continuous function learned by MLP, which corresponds to the Monte Carlo approximation of the continuous convolution.
- This operation is called **PointConv**.

## Formulation / Solver / Implementation
- PointConv involves taking the positions of point clouds as input and uses a MLP to learn approximate a weight function, as well as applying a inverse density scale on the learned weights to compensate the non-uniform sampling.

## Useful info / tips


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

# Specs

