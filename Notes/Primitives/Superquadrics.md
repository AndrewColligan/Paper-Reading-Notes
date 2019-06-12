# Basic info
- Title: Superquadrics Revisited: Learning 3D Shape Parsing beyond Cuboids
- Author: Despoina Paschalidou, Ali Osman Ulusoy & Andreas Geiger
- Affiliation: Autonomous Vision Group, MPI for Intelligent Systems Tubingen & Microsoft &  University of Tubingen & Max Planck ETH Center for Learning Systems
- Publication status: CVPR 2019
- Short name: Superquadrics
- Year: 2019

# Score
- Idea: 5
- Usability: 5
- Presentation: 5
- Overall: 5

# Contributions
## Problem addressed / Motivation
- Abstracting complex 3D shapes with parsimonious part-based representations has been a long standing goal in computer vision.

## Idea / Observation / Contribution
- Utilises superquadrics as primitives instead of 3D cuboid representations.
- This leads to more expressive 3D scene parses while being easier to learn than 3D cuboid representations.
- Provide a solution to the Chamfer loss which avoids the need for computational expensive reinforcement learning or iterative prediction.

<p align="center">
  <img src="https://ps.is.tuebingen.mpg.de/uploads/publication/image/22555/superquadrics_parsing.png" width=500>
</p>

## Formulation / Solver / Implementation
- Unsupervised method.
- Network uses a voxelised input and consists of an encoder with 5 layer convolutional layers, followed by a fully connected layer, then 5 regressor final layers predicting the size (&alpha;), shape (&epsilon;), translation (t), rotation (q) and probability of existence (&gamma;) in continuous space.
- The reconstruction loss measures the difference between the predicted shape and the target shape.
- The Chamsfer distance is used where the distance from the predicted primitive and the point cloud is measured and vice versa. The loss of each of these is added together.
- A set of points is sampled from the continuous surface of the primitive.
- There is also a parsimony loss to encourage sparity.

## Useful info / tips
- The probability of existence (&gamma;) uses the Bernoulli distribution to predict if a primitive is part of the scene (i.e. z<sub>m</sub>=1) or not (i.e. z<sub>m</sub>=0).

# Evaluation
## Dataset
- ShapeNet
- SURREAL human body dataset

## Metrics
- Superquadrics define a family of parametric surfaces that can be fully described by a set of 11 parameters.
- To further increase parsimony, they fixed all parameters expcept &gamma; for additional 5k iterations. This step removed remaining overlapping primitives.
- Voxel resolution of 32<sup>3</sup>.
- Maximum number of primitives M = 20.

## Results
- The results show that for any given number of primitives, superquadrics consistently achieve a lower loss, and hence a higher modeling fidelity.

# Resource
## Paper
https://arxiv.org/abs/1904.09970

## Project page
https://ps.is.tuebingen.mpg.de/publications/paschalidou2019cvpr

## Source code
https://github.com/paschalidoud/superquadric_parsing

## Questions
- Can we use a similar regressor approach for the Prime Primitives?

