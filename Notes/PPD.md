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
	1. The problem of physical primitive decomposition - learning of compact, disentangled primitives.
	2. Present a novel learning paradigm that learns to characterise shapes in physical primitives to explain both their geometry and physics.
	3. Demonstrate that their system can achieve good performance on both synthetic and real data.

## Formulation / Solver / Implementation
- Evaluates their system for physical primitive decomposition in three scenerios:
	1. **Decomposing Block Towers**: They generate a dataset of synthetic block towers, where each block has distinct geometry and physics. The model recontructs the physical primitives by making use of both appearance and motion cues.
	2. **Decomposing Tools**: They evaluate the system in a set of synthetic tools, demonstrating its applicability to daily-life shapes.
	3. **Decomposing Real Objects**: They built a new dataset of real block towers in dynamic scenes, and evaluated the model's generalisation power to real videos.
	
- Ablation studies are also presented to understand how each source of information contributes to the final performance.
- Human behavioral experiments to contrast the performance of the model compared with humans is undertaken, where the question of 'which block is heavier' is asked.
	
<p align="center">
	<img src='https://media.springernature.com/original/springer-static/image/chp%3A10.1007%2F978-3-030-01258-8_1/MediaObjects/474200_1_En_1_Fig5_HTML.gif' width=500'>
</p>

## Useful info / tips
- Ablation study refers to removing some feature of the model or algorithm, and seeing how that affects performance.

# Evaluation
## Dataset
- Texture for materials is obtained by cropping the center portion of images from the MINC dataset.
- 3D Warehouse, where the unrelated models were manually removed.

## Metrics
- Network CNN encoder input is: voxels (32<sup>3</sup> grid), images and object trajectories.
- Predicted metrics: size = *(s<sub>x</sub> s<sub>y</sub>, s<sub>z</sub>)*, position = *(p<sub>x</sub>, p<sub>y</sub>, p<sub>z</sub>)*, rotation in quaternion form = *(q<sub>w</sub>, q<sub>x</sub>, q<sub>y</sub>, q<sub>z</sub>)* and density.
- Shape parameters are continuous real values, where density is a discrete value. Therefore, the density value is discretised into N<sub>D</sub> = 100 slots, so that estimating desnity becomes a N<sub>D</sub>-way classification.
- The voxel feature, image feature and trajectory feature are concatenated together and mapped to a low dimensional feature using a fully-connected layer. The set of physical primitives are sequentially predicted by a recurrent generator.
- Loss function consists of a geometry loss and physics loss.

### Decomposing Block Towers
- The performance of shape reconstruction by the F1 score between the prediction and ground truth is used. Each primitive in prediction is labeled as a true positive if its IoU with a ground-truth primitive is greater than 0.5. 
- For physics estimations, they employed two types of metrics i) density measures top-k accuracy and root-mean-square error (RMSE) and ii) trajetory measure: mean-absolute error (MAE) between simulated trajectory (using predicted physical parameters) and ground-truth trajectory.

### Decomposing Tools
- Perform PCA on the point clouds and align models by their PCA axes.
- Use energy-based optimisation to fit the primitives from the point cloud, and assign each vertex to its nearest primitive and refine each primitive with the minium oriented bounding box of vertices assigned to it.
- Pre-train model on their PPD model due to there being less training examples.


### Decomposing Real Objects
- Purchased sets of blocks with different materials from Amazon.
- Block tower is placed at a specific position on the desk, and they used a copper ball (hung by a pendulum) to hit the tower.
- The appearance of every fram in RGB video is used to extract a 3D trajectory, by using **2D keypoint tracking** and **3D pose reconstruction**.

## Results
### Decomposing Block Towers
- For shape reconstruction, the model achieves 97.5 in terms of F1 score.
- For physics estimation, experiments suggest that appearance alone is not sufficient for density estimation.
- When combining with object trajectories, the estimation of the density is much better.

### Decomposing Tools
- 85.9 in terms of F1 score.
- The shape recontruction is not as good as that of the block towers dataset because the synthetic tools are more complicated, and orientations might introduce some ambiguity.
- The physics estimation is better since there are less primitives in the synthetic tool dataset.

### Decomposing Real Objects
- The model cannot effectively predict the physical parameters because images and object trajectories are much noiser than those in synthetic dataset.
- RMSE = 18.7 over the whole dataset and 10.1 over block towers with two blocks.

# Resource
## Project page
- Paper: https://arxiv.org/abs/1809.05070

## Dataset
- 3D Warehouse: https://3dwarehouse.sketchup.com

## Build Upon
- Use combination of multiple networks learning different information for CSGNet paper.

## Paper connections
- Primitives

## Software
- Binvox
- Blender
- Bullet Physics Engine
