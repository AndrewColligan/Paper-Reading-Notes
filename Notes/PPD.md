# Basic info
- Title: Physical Primitive Decomposition
- Author: Zhijian Liu, William T. Freeman, Joshua B. Tenenbaum and Jiajun Wu
- Affiliation: Massachusetts Institute of Technology, Google Research
- Publication status: European Conference on Computer Vision (ECCV 2018)
- Short name: PPD
- Year: 2018

# Score
- Idea: 5
- Usability: 4
- Presentation: 5
- Overall: 4

# Contributions
## Problem addressed / Motivation
- Objects are made of *functional parts*, each with distinct geometry, physics, functionality, and affordances. 
- For intelligent agents to better explore and interact with the world, there must be development of a distributed, physical, interpretable representation of objects.
- Goal is to explain the shape and physics of an object with shape primitives with physical parameters.

<p align="center">
	<img src='http://ppd.csail.mit.edu/images/ppd.jpg' width=500>
</p>

## Idea / Observation / Contribution
- Proposed a formulation that learns a part-based object representation from both **visual observations** and **physical interactions**. Starting from a single image and a voxelised shape, the model recovers the geometric primitives and infers their physical properties from texture.
- The contributions include:
	1. The problem of physcial primitive decomposition - learning of compact, disentangled primitives.
	2. Present a novel learning paradigm that learns to characterise shapes in physical primitives to explain both their geometry and physics.
	3. Demonstrate that their system can achieve good performance on both synthetic and real data.

## Formulation / Solver / Implementation
- Evaluates their system for physical primitive decomposition in three scenerios:
	1. They generate a dataset of synthetic block towers, where each block has distinct geometry and physics. The model recontructs the physical primitives by making use of both appearance and motion cues.
	2. They evaluate the system in a set of synthetic tools, demonstrating its applicability to daily-life shapes.
	3. They built a new dataset of real block towers in dynamic scenes, and evaluated the model's generalisation power to real videos.
	
- Ablation studies are also presented to understand how each source of information contributes to the final performance.
- Human behavioral experiments to contrast the performance of the model compared with humans is undertaken, where the question of 'which block is heavier' is asked.
	
<p align="center">
	<img src='https://media.springernature.com/original/springer-static/image/chp%3A10.1007%2F978-3-030-01258-8_1/MediaObjects/474200_1_En_1_Fig5_HTML.gif' width=500'>
</p>

## Useful info / tips
- Ablation study refers to removing some feature of the model or algorithm, and seeing how that affects performance.

# Evaluation
## Dataset


## Metrics
- Network CNN encoder input is: voxels (32<sup>3</sup> grid), images and object trajectories.
- Predicted metrics: size = *(s<sub>x</sub> s<sub>y</sub>, s<sub>z</sub>)*, position = *(p<sub>x</sub>, p<sub>y</sub>, p<sub>z</sub>)*, rotation in quaternion form = *(q<sub>w</sub>, q<sub>x</sub>, q<sub>y</sub>, q<sub>z</sub>)* and density.
- Shape parameters are continuous real values, where density is a discrete value. Therefore, the density value is discretised into N<sub>D</sub> = 100 slots, so that estimating desnity becomes a N<sub>D</sub>-way classification.
- The voxel feature, image feature and trajectory feature are concatenated together and mapped to a low dimensional feature using a fully-connected layer. The set of physical primitives are sequentially predicted by a recurrent generator.
- Loss function consists of a geometry loss and physics loss.
- The performance of shape reconstruction by the F1 score between the prediction and ground truth is used. Each primitive in prediction is labeled as a true positive if its IoU with a ground-truth primitive is greater than 0.5. For physics estimations, they employed two types of metircs i) density measures top-k accuracy and root-mean-square error (RMSE) and ii) trajetory measure: mean-absolute error (MAE) between simulated trajectory (using predicted physical parameters) and ground-truth trajectory.

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

# Software
- Binvox
