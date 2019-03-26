# Basic info
- Title: OctNet: Learning Deep 3D Representations at High Resolutions
- Author: Gernot Riegler, Ali Osman Ulusoy & Andreas Geiger
- Affiliation: Institute for Computer Graphics and Vision, Graz University of Technology, Autonomous Vision Group, MPI for Intelligent Systems Tubingen & Computer Vision and Geometry Group, ETH Zurich.
- Publication status: 2017 IEEE Conference on Computer Vision and Pattern Recognition (CVPR)
- Short name: OctNet
- Year: 2017

# Score
- Idea: 4
- Usability: 4
- Presentation: 5
- Overall: 4

# Contributions
## Problem addressed / Motivation
- Increased access to 3D data.
- Most existing 3D learning methods utilise voxels where computational and memory requirements increase cubically with an increase in resolution.
- From voxel tests, it was shown that high activations occur only near the object boundaries.

## Idea / Observation / Contribution
- Propose OctNet, a 3D convolutional network that exploits the sparsity property of 3D data.
- 3D space hierarchically partitioned into a set of unbalanced octrees; where each octree solits the 3D scaoe according to density.
- OctNet demonstrated on three different problems:
  1. 3D classification.
  2. 3D orientation estimation of unknown object instances.
  3. Semantic segmentation of 3D point clouds.
  
<p align="center">
  <img src="https://www.is.mpg.de/uploads/publication/image/18921/img03.png" width=500>
</p>

## Formulation / Solver / Implementation
- A hybrid grid octree data structure utilised to overcome limitation of vanila octree.
- The maximal depth is restricted to a small number e.g. three, and several shallow octrees are placed along a regular grid.
- Method not as memory efficient as a standard octree, but significant compression ratios can be achieved.
- Shallow octrees can be encoded efficiently using a bit string representation which further lowers access time and allows for efficient GPGPU implementations.
- Studied effects of input resolution on memory usage, runtime and classification accuracy.

## Useful info / tips
- Unfortunately, vanilla octree implementations have several drawbacks that hamper its application in deep networks:
  1. While octrees reduce the memory footprint of the 3D representation, most versions do not allow for efficient access to the underlying data. In particular, octrees are typically implemented using pointers, where each node contains a pointer to its children. Accessing an arbitrary element (or the neighbour of an element) in the octree requires a traversal starting from the root until the desired cell is reached. Thus, the number of memory accesses is equal to the depth of the tree. This becomes increasingly costly for deep, high resolution octrees.
  2. Convolutional network operations such as convolution or pooling require frequent access to neighboring elements. It is thus critical to utilize an octree design that allows for fast data access.

# Evaluation
## Dataset
- ModelNet10
- RueMonge2014

## Metrics
- Input: triangular mesh convert to octree.
- Input resolution: 8<sup>3</sup> to 256<sup>3</sup> voxels.
- For 3D semantic segmentation, an autoencoder is used.

## Results
- Important information near the surface of part.
- For 3D orientation estimation, it is seen that the accuracy increases with an increase in resolution.

#### Semantic Segmentation on RueMonge2014

| Network         | Average  | Overall  | IoU      |
| --------------- | -------- | -------- | -------- |
| 64<sup>3</sup>  | 60.0     | 73.6     | 45.6     |
| 128<sup>3</sup> | 65.3     | 76.1     | 50.4     |
| 256<sup>3</sup> | **73.6** | **81.5** | **59.2** |

# Resource
## Paper
https://arxiv.org/pdf/1611.05009.pdf

## Source code
https://github.com/griegler/octnet

## Questions
- Is this approach of forming an octree different from O-CNN?

## Build upon
- Learning for multi-view 3D reconstruction where the ability to process high resolution voxelised shapes is of crucial importance.

## Paper connections
- Octree
- CNN

## Software & Hardware
- C++
- CUDA
- Torch
- GPU memory: 12GB for 256<sup>3</sup>
