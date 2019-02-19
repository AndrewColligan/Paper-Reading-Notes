# Basic info
- Title: 3D-PRNN: Generating Shape Primitives with Recurrent Neural Networks
- Author: Chuhang Zou, Ersin Yumer, Jimei Yang, Duygu Ceylan, Derek Hoiem
- Affiliation: University of Illinois at Urbana-Champaign, Adobe Research
- Publication status: 
- Short name: 3D-PRNN
- Year: 2017

# Score
- Idea: 
- Usability: 
- Presentation: 
- Overall: 

# Contributions
## Problem addressed / Motivation
- Robotics and graphics application require 3D interpretations of sensory data.
- Challenge to represent 3D object geometry so that:
	1. Noisy and partial observations can be predicted.
	2. It is useful for reasoning about extent, contact and support etc.
	
## Idea / Observation / Contribution
- Use of 3D primitves instead voxels as it is more **compact**.
- Primitives are also **holistic**, representing an object in few parts, which simplifies reasoning about stability, connectedness and other properties.
- Contribution is to learn 3D primitives representations of objects from unannotated 3D meshes.
- Method to fit primitves from **point clouds**.

<img src='https://github.com/zouchuhang/3D-PRNN/raw/master/figs/teasor.jpg' width=400>

## Formulation / Solver / Implementation
- Autoencoder architecture.
- RNN to encode an implicit shape representation and then decode into a sequence of generated primitives to approximate the shape.
- Ground truth data acquired by method based on **Gaussian Fields** and **energy minimization** to iteratively parse shapes into primitive components.
- Optimise a differentiable loss function using robust techniques (L-BFGS).
- The network is trained jointly with a single depth image and a sequence of primitives configurations (shape, translation and rotation) that form the complete shape.

## Useful info / tips
- Utilised symmetry of man-made objects to speed up primitive parsing procedure.
- Predicts shapes with aggregations of primitives that has the benefit for lower computational and storage costs.
- Network predicts for each primitive, its shape (height, length, width), position (i.e. translation) and orientation (i.e. rotation).
- Additionally, at each step, a binary *end of generation* signal is predicted which indicates no more primitive should be generated.

# Evaluation
## Dataset
- 3 classes containing models of chairs, tables and drawers.
- NYU Depth V2.

## Metrics
- To produce parameterised 3D primitives (oriented cuboids), the RNN was customised to encode explicit geometric constraints of symmetry and rotation. 
- Separately predicting whether a primitive should rotate along each axis and by how much improves results over more simply predicting rotation values, since many objects consist of several (unrotated) cuboids.
- For optimisation, during each iteration they randomly initialise 10 primitives, optimise for each of these primitives and add the best fitting primitives to the primitive collection.
- RNN = LSTM with Leaky Relu.
- To avoid **overfitting**, 15% of training samples were held to choose the number of training epochs. The network is then retrained using the entire training set.
- Pre-sort primitives based on the height of each shape center in a decreasing fashion, to reduce randomness that make training harder.
- ADAM optimiser.
- IOU and surface-to-surface distance (computed using 5,000 points sampled on the primitive and ground truth surfaces amd the distance is normalised by the diameter of a sheere tightly fit to the ground truth mesh) used for accuracy.

## Results
- By enforcing rotation axis contraints ("3D-PRNN + rot loss"), achieves better performance.
- 3D-PRNN outperforms kNN Baseline.
- Wu et al performs similarly on IoU measure and better on surface distance, which is less sensitive to alignment, but more sensitive to details in structures.
- Was also able to be used in shape segmentation.
- Capable of modelling shapes with fewer training examples available.
- Higher degree of freedom representations can be achieved.

# Resource
## Paper
https://arxiv.org/abs/1708.01648

## Source code
https://github.com/zouchuhang/3D-PRNN

# Build upon
- Look into method's code for using point cloud.

# Key Words
- Primitives
- RNN
