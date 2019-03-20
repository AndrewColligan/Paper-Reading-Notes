# Basic info
- Title: NormalNet: A voxel-based CNN for 3D object classification and retrieval
- Author: Cheng Wang, Ming Cheng, Ferdous Sohel, Mohammed Bennamoun, Jonathan Li
- Affiliation: 
  1. Fujian Key Laboratory of Sensing and Computing for Smart City, School of Information Science and Engineering, Xiamen University, Xiamen, China
  2. Murdoch University, Perth, Australia
  3. The University of Western Australia, Perth, Australia
  4. Department of Geography and Environmental Management, University of Waterloo, Waterloo, Canada.
- Publication status: Journel of Neurocomputing - Volume 323, 5 January 2019, Pages 139-147
- Short name: NormalNet
- Year: 2019

# Score
- Idea: 
- Usability: 
- Presentation: 
- Overall: 
                                                                                                                
# Contributions
## Problem addressed / Motivation
- It has been shown that the accuracy of models does not drastically increase with increased resolution.
- The amount of information in 3D data is not necessarily larger than 2D data.
- 3D shapes are defined on its surface and in a 3D occupancy grid each voxel is binary, whereas a 2D pixel has 256 gray level.

## Idea / Observation / Contribution
- First to propose a voxel-based CNN with normal vectors as input.
- Normal vector should contain more information like position and orientation of the model surface.
- Designed a reflection-convolution-concatenation (RCC) module for conv layer, that achieves higher classification accuracy than ordinary conv layer with fewer parameters.

<p align="center">
          <img src="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Imgs/normalnet.jpeg" width=300>
</p>

## Formulation / Solver / Implementation
- RCC module generates feature maps by both conv kernels and their reflections.
- In the RCC module, parameters are shared not only between different receptive fields, but also between the input and its reflections. This reduces the number of parameters in the output layer by two-thirds.
- The conv kernel is reflected instead of the input, as if the input had different sizes across dimensions, a second reflection would be required before conctenation.
- Model rotation is used as a data augmentation method to increase training samples and reduce overfitting.
- Combine two networks, which take normal vectors and voxels as inputs respectively, and train them synchronously using the network fusion technique.

## Useful info / tips
- In the process of voxelisation, each path of CAD model is split iteratively until all vertices fall into the same voxel, then the value of the voxel is set to 1.
- At training time, the rotations of the same model are deemed to be different training samples.
- **Hard parameter sharing** - the hidden layers are shared between all tasks while keeping several task-specific output layers, which greatly reduces the risk of overfitting.
- **Soft parameter sharing** - each task has its own model with its own parameters, while the distance between the parameters is regularised to encourage the parameters to be similar.

# Evaluation
## Dataset
- ModelNet40
- ModelNet10
- Sydney Urban Objects Dataset

## Metrics
- Store normal vector as *signed char type* instead of *float type* due to the storage costs being 1 byte per normal instead of 12.
- 30<sup>3</sup> voxel resolution.
- Classification losses are computed using softmax and cross entropy.
- Two forms of RCC-I & RCC-II which have 12  and 20 rotation augmentations respectively along the z-axis.
- Two fusion strategies - hard parameter sharing and cross-stitch networks (CSNs).

## Results
- Conclude that CSN was better.
- ModelNet40 Classification: 88.8%.
- ModelNet10 Classification: 93.5%.
- Sydney Urban Objects Dataset Classification: 0.74 average F1.
- ModelNet40 Retrieval: 84.4% mAP.

# Resource
## Paper
https://www.sciencedirect.com/science/article/pii/S0925231218311561

## Paper connections
- CNN
- Voxels
- Normals

## Software & Hardware
- NVidia Titan X
