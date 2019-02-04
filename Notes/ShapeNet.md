# Basic info
- Title: 3D ShapeNets: A Deep Representation for Volumetric Shapes
- Author: Zhirong Wu, Shuran Song, Aditya Khosla, FIsher Yu, Linguang Zhang, Xiaoou Tang, Jianxiong Xiao
- Affiliation: Princeton University, Chinese University of Hong Kong, Massachusetts Institute of Technology
- Publication status: 2015 IEEE
- Short name: ShapeNet

# Score
- Idea: 5
- Usability: 3
- Presentation: 4
- Overall: 4

# Contributions
## Problem addressed / Motivation
- 3D shape is not used in any state-of-the-art recognition methods, due to a lack of good generic representation of 3D geometric shapes.
- With availablilty of inexpensive 2.5D depth sensors (e.g. Microsoft Kinect), 3D shape representation is becoming more important.

## Idea / Observation / Contribution
- Development of ModelNet dataset.
- First paper to propose the representation of 3D geometric shape as a probability distribution of binary variables on a 3D voxel grid for full 3D deep learning.
- Object recognition and shape completion.
- Compute the potential information gain for recognition with regard to missing parts. Allows for the choosing of optimal subsequent view for observation if first view does not produce large enough confidence.

![ShapeNet](https://camo.githubusercontent.com/35839c3e3ad4a4cc43412b0deef4a740cbc32909/68747470733a2f2f6169322d73322d7075626c69632e73332e616d617a6f6e6177732e636f6d2f666967757265732f323031362d31312d30382f336564323333383632383461353633396362336538626161656366343936636161373636653333352f312d466967757265312d312e706e67 "ShapeNet")



## Formulation / Solver / Implementation
- Convolutions used to reduce number of model parameters, due to the shared weights.
- Convolutional Deep Belief Network
- The **Next-Best-View** problem is considered at the precise voxel level allowing them to infer how voxels in a 3D region would contribute to the reduction of recognition uncertainty.
- Model pre-trained in a **layer-wise fashion** followed by a **generative fine-tuning procedure**.
- During pre-training, the first four layers are trained using standard **Contrastive Divergence**, while the top layer is trained more carefully using **Fast Persistent Contrastive Divergence** (FPCD).
- Fine-tuning procedure is similar to wake-sleep algorithm, except the weights are tied.
- During pre-training of first layer, learning signal to receptive fields which are non-empty are collected, due to empty spaces containing no information which distracts learning.

## Useful info / tips
- Each 3D mesh is representated as a binary tensor.
- 1 means the voxel is inside the mesh surface and 0 means the voxel is outside the mesh surface (i.e. it is empty space).

![Image of ShapeNet Network](http://3dshapenets.cs.princeton.edu/teaser.jpg "ShapeNet Network")

# Evaluation
## Dataset
- ModelNet (own dataset) - 151,128 3D CAD models, with 660 unique object categories.
- ModelNet10: 4899 models from 10 categories. 
- ModelNet40: 12311 models from 40 categories, all are uniformly orientated.

## Metrics
- 30 x 30 x 30 voxel resolution.
- 3D shape represented by 24 x 24 x 24 voxel grid with 3 extra cells of padding in both directions to reduce convolution border artifacts.

## Results

# Resource
## Project page
http://3dshapenets.cs.princeton.edu/

## Source code
https://github.com/zhirongw/3DShapeNets

## Dataset
http://3dshapenets.cs.princeton.edu/

## Other paper reading notes

## Others

# Questions


# Build upon


# Paper connections
- Voxels
- Convolutional Deep Belief Network

# Specs
- Intel XEON E5-2690 CPU
- NVIDIA K40c GPU

