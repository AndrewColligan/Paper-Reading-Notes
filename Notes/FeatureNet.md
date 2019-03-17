# Basic info
- Title: FeatureNet: Machining feature recognition based on 3D Convolutional Neural Network
- Author: Zhibo Zhang, Prakhar Jaiswal, Rahul Rai
- Affiliation: Manufacturing and Design (MAD) Lab, Department of Mechanical and Aerospace Engineering, University of Buffalo
- Publication status: Journel of Computer-Aided Design
- Short name: FeatureNet
- Year: 2018

# Score
- Idea: 2
- Usability: 3 
- Presentation: 5
- Overall: 3

# Contributions
## Problem addressed / Motivation
- Disconnect between CAD and CAM. 
- CAPP is focussed on generating a set of manufacturing operations to fabricate a given part specified by its CAD model. 
- CAPP has to interpret a given CAD model in terms of *features*, to reason about the fabrication instructions.
- Features are semantically higher level geometric elements such as hole, slot and pocket etc.
- Use current feature recognition limitations:
	1. Inability to learn and generalise.
	2. Lack of tolerance to noise in the input CAD models.
	3. Computationally intensive and inflexible.
	4. Focused on specific types of CAD representation and thus not generalisable in cases where interoperability between different geometric representation is required.
	5. Limited in ability to handle feature variations.

## Idea / Observation / Contribution
- Novel framework using Deep 3D-CNNs to learn machining features from a CAD model of mechanical parts is presented.
- To train the developed 3D deep learning model, a large-scale machining feature dataset with 3D CAD models, termed FeatureNet database is automatically constructed.
- The strength of the learned deep learning model at recognising complex machining features in various 3D CAD model is demonstrated.

## Formulation / Solver / Implementation
- Voxel
- Deep 3D Convolutional Neural Networks (3D-CNNs).
- Network only recognises **non-intersecting** features that are the only feature on the CAD model.
- To recognise multiple features on a CAD model, features are segmented using **watershed segmentation algorithm**.
- Each segmented feature is then passed through the trained model for recognition.

<p align="center">
	<img src="https://github.com/zibozzb/FeatureNet/raw/master/img/1.png" alt="FeatureNet Network" align="middle" width="800">
</p>

## Useful info / tips
- Due to discretization of input models into voxels, small noise has little effect on performance.
- Discretization itself causes *stair-stepping noise* and can lead to incorrect classification. This can be reduced by increasing the resolution.

# Evaluation
## Dataset
- Created by using Solidworks API.
- 24000 models belonging to 24 classes.
- 6000 different samples at 6 orientations.

<p align="center">
	<img src="https://github.com/zibozzb/FeatureNet/raw/master/img/2%20(1).png" alt="FeatureNet Dataset" align="middle" width="400">
</p>

## Metrics
- 64 x 64 x 64 voxel grid
- Voxel values were normalised by zero-centering to {-1, 1}.
- Training: 70%, Validation: 15%, Testing:15%.
- Batch size: 40.
- Optmiser: ADAM.

## Results
- Training Accuracy: 99.95%, Validation Accuracy: 97.46%, Testing Accuracy: 96.70%.
- Segmentation Accuracy: 94.21%.

# Resource
## Source code
https://github.com/zibozzb/FeatureNet

## Dataset
https://github.com/zibozzb/Machining-feature-dataset


# Build upon
- More complex network could be used.
- Different representation.
- Multiple trained 3D CNN's could be used simultaneously to reason about manufacturability of a given 3D CAD model using different **manufacturing processes**.
- Integrate the tasks of segmentation and classification.
- By restructuring the CNN architecture and training on large multi-feature dataset, both of these tasks can be performed simultaneously by the CNN.

# Key Words
- Voxel
- CAPP

# Equipment & Software
- Tensorflow
- Binvox
- Intel i7 processor (2.60GHz)
- 16 GB RAM
- NVIDIA GeForce GTX 960M
