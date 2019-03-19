# Basic info
- Title: Learning localized features in 3D CAD models for manufacturability analysis of drilled holes
- Author: Sambit Ghadai, Aditya Balu, Soumik Sarkar, Adarsh Krishnamurthy
- Affiliation: Department of Mechanical Engineering, Iowa State University, IA, USA
- Publication: Journel of Computer Aided Geometric Design
- Short name: DLDFM
- Year: 2018

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
- Voxel-based occupancy grid representation do not have information on the surfaces of objects without additional processing.
- Also not robust enough to capture information about the location, size or shape of a feature within an object.

## Idea / Observation / Contribution
- Feature identification framework for recognising *difficult-to-manufacture* drilled holes.
- Local features of 3D voxelised CAD models are recognised using a 3D-CNN.
- Normal information of surfaces also used in addition to volume occupancy information.
- 3D-GradCAM (3D-CNN based gradient-weighted class activation mapping) is used to provide visually display the difficult-to-manufacture features outputed by the network.
- GPU-accelerated methods for converting CAD models to volume representations (voxelisation augmented with surface normals).

<p align="center">
	<img src="https://ars.els-cdn.com/content/image/1-s2.0-S0167839618300384-gr002.jpg">
</p>

## Formulation / Solver / Implementation
- DLDFM (Deep Learning Design For Manufacturing) framework, used the following DFM rules to create synthetic dataset:
	1. **Depth-to-diameter ratio**: The depth-to-diameter ratio should be less than 5.0 for the machinability of the hole.
	2. **Through holes**: Since a through hole can be drilled from both directions, the depth-to-diamter ratio for a through hole should be less than 10.0 to be manufacturable.
	3. **Holes close to the edges**: A manufacturable hole should be surrounded with material of thickness at least equal to the half the diamter of the hole.
	4. **Thin sections in the depth direction of the hole**: A manufacturable hole should have material greater than half the diamter along the depth direction.
- To create voxel model, a grid of voxels in the region occupied by the object are constructed.


# Evaluation
## Dataset
- Automatically generated cubes with single hole features in each, with a label of manufacturable or non-manufacturable.
- 9531 CAD models (75% -> training, 25% -> validation)
- 675 CAD models (testing)


## Metrics
- 64 x 64 x 64 voxel grid
- Batch size = 64
- Optimizer = Adadelta
- Loss Function = Binary Cross-Entropy
- CNN (2 Convolutional layers, 2 max pooling layer & 1 fully connected layer)

## Results
**Quantitative performance of the DLDFM on test data sets**

| Test Data Type | Model Description             | True Positive | True Negative | False Positive | False Negative | Accuracy  |
| -------------- | ----------------------------- | ------------- | ------------- | -------------- | -------------- | --------  |
| 675 models     | In-outs                       | 391           | 90            | 17             | 176            | 0.7136    |
| 408 manufacturable | In-outs + surface normals | 334           | 201           | 74             | 65             | **0.7938**|

---
**DLDFM detection of manufacturability**
<p align="center">
	<img src="https://ars.els-cdn.com/content/image/1-s2.0-S0167839618300384-gr009.jpg" width = 500>
</p>

# Resource
## Project page
https://www.sciencedirect.com/science/article/pii/S0167839618300384

## Source code
For the creation of voxelised GPU-accelerated models
https://github.com/idealab-isu/GPView

# Questions
- Can surface normals be used with CSGNet paper for more information.

# Build upon
- Train additional networks for different manufacturing processes.

# Paper connections
- 3D-CNN

# Equipment & Software
- Kera with Tensorflow
- 128GB CPU RAM
- NVIDIA Titan X GPU with 12GB GPU RAM
