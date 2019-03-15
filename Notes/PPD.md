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

<p align="center">
	<img src='http://ppd.csail.mit.edu/images/ppd.jpg' width=500>
</p>

## Idea / Observation / Contribution
- Proposed a formulation that learns a part-based object representation from both **visual observations** and **physical interactions**.
- The contributions include:
	1. The problem of physcial primitive decomposition - learning of compact, disentangled primitives.
	2. Present a novel learning paradigm that learns to characterise shapes in physical primitives to explain both their geometry and physics.
	3. Demonstrate that their system can achieve good performance on both synthetic and real data.

## Formulation / Solver / Implementation
- Deep 3D Convolutional Neural Networks (3D-CNNs).

## Useful info / tips
- Large-scale shape repositiories like ShapeNet have limited annotations on object parts due to:
	1. Annotating objects and physics being labour-intensive and requiring good domain expertise.
	2. There exists intrinsic ambiguity in the ground truth: it is impossible to precisely label underlying physical object properties like densities only by images or videos.

# Evaluation
## Dataset


## Metrics


## Results


# Resource
## Project page


## Source code


## Dataset
- ModelNet
- 

## Other paper reading notes

## Others

# Questions


# Build upon


# Paper connections


