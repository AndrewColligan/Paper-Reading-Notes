# Basic info
- Title: FusionNet: 3D Object Classification Using Multiple Data Representation
- Author: Vishakh Hegde, Reza Zadeh
- Affiliation: Matroid Inc. and Standford University
- Publication status: 
- Short name: FusionNet

# Score
- Idea: 3
- Usability: 4
- Presentation: 3
- Overall: 3

# Contributions
## Problem addressed / Motivation
- High-quality 3D object recognition is important for the future of computer vision and robotic systems.
- CNN require lots of data, however amount of 3D data is currently lacking.
- The amount of 3D content creation publicily available is rapidly increasing.
- Content created for augmented reality and self driving cars.

## Idea / Observation / Contribution
- Combine volumetric voxel representation and 2D multi-view representation for training relatively weak classifiers.
- Hybrid network to achieve higher accuracy than individual methods.
- One of the Volumetric CNN has 3.5 million parameters compared to AlexNet which has 60 million parameters.


- Introduce two new CNNs for volumetric data, with one having significantly less number of parameters compared to standard CNNs used on 2D RGB images such as AlexNet.
- One of the networks uses an inception module used in GoogLeNet.
- This utilises transfer learning from pre-trained network on large ImageNet dataset for the multi-view representation and uses the volumetric information.

## Formulation / Solver / Implementation
- Convolutional Neural Network.
- Two CNNs for volumetric data which combine information from multiple orientations by max-pooling across 60 orientations.
- Both networks use long range 3D convolutions which aggregate information across a dimension of the object.
- In one network, the output is concatenated from kernels of various sizes, similar to the inception module used by GoogLeNet.

- For pixel data, use idea from Multi View CNN (MV-CNN) of taking multiple projected views of the same 3D and combine them to improve the performance over a single projection.
- For voxel data, network used on multiple orientations of all objects in the training set to learn features which are partly complementary to those learned for pixel data.
- Combine multiple networks in the final fully connected layer which outputs classification accuracy are over each of its component networks.


## Useful info / tips
- 

# Evaluation
## Dataset
- 3D model classification has been limited due to unavailability of large scale training sets like ImageNet.
- ModelNet10: 3991 CAD models for training, 908 CAD models for testing, 10 classes
- ModelNet40: 12311 distinct CAD models, 9843 models for training, 2468 models for testing, 40 classes


## Metrics


## Results


# Resource
## Project page
https://arxiv.org/abs/1607.05695

## Source code


## Dataset


## Other paper reading notes

## Others

# Questions


# Build upon

# Key Words
- CNN
- Voxels
- Multi View


# Paper connections


