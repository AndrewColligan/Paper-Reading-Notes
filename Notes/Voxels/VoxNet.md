# Basic info
- Title: VoxNet: A 3D Convolutional Neural Network for Real-Time Object Recognition
- Author: Daniel Maturana and Sebastian Scherer
- Affiliation: Robotics Institute, Carnegie Mellon University, USA
- Publication status: 2015 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS) 
- Short name: VoxNet
- Year: 2015

# Score
- Idea: 3
- Usability: 2
- Presentation: 4
- Overall: 3

# Contributions
## Problem addressed / Motivation
- Robust object recognition is required for autonomous robots operating in real world environments.
- Modern robotic systems have sensors such as LiDAR and RGBD cameras that provide greater 3D information; able to help in this task.
- Current systems do not fully utilise this information and have touble with large amounts of point cloud data.

<p align="center">
	<img src="http://dimatura.net/research/voxnet/car_voxnet_side.png" width=500>
</p>
	
## Idea / Observation / Contribution
- Propose VoxNet, an architecture integrating a volumetric occupancy grid (voxel) representation with a supervised 3D CNN.
- Can operate on LiDAR, RGBD and CAD data.

## Formulation / Solver / Implementation
- Point cloud data converted to voxels.
- Voxel can be stored and manipulated with simple and efficient data structures, for this work, dense arrays were used.
- To keep larger spatial extents in memory, hierarchical data structures were used and specific segments are copied to dense arrays as needed. This theoretically allows for a potentially unbounded volume to be stored while using small occupancy grids for CNN processing.
- Each point *(x,y,z)* is mapped to a discrete voxel coordinate *(i,j,k)*.
- 3D ray tracing used to calculate the number of hits and pas-trhoughs for each voxel.
- Given this information there are three different occupancy grid models to estimate occupancy:
	1. **Binary occupancy grid** - in this model, each voxel is assumed to have a binary state, occupied or unoccupied.
	2. **Density grid** - in this model, each voxel is assumed to have a continuous density, corresponding to the probability the voxel would block a sensor beam.
	3. **Hit grid** - this model only consider hits, and ignores the difference between unknown and free space. This model discards some potentially valuable information, however it does not require raytracing, which is useful in computationally constrained situations.
- At training time, each input instance is rotated 360&deg;/n intervals aroung the *z* axis.
- At test time, they pool the activations of the output layer over all *n* copies.

## Useful info / tips
- Volumetric representation is richer than point clouds, as it distinguishes free space from unknown space.
- Feature based point clouds often require spatial neighbourhood queries, which can quickly become intractable with large numbers of points.

# Evaluation
## Dataset
- LiDAR: Sydney Urban Objects.
- CAD data: ModelNet.
- RGBD data: NYUv2.

## Metrics
- 32<sup>3</sup> voxel grid.
- Two voxel resolution methods: 
	1. For LiDAR dataset, a fixed spatial resolution is used e.g. voxels of (0.1m)<sup>3</sup>. This maintains the information given by the relative scale of the object
	2. The resolution is chosen so the object of interest occupies a subvolume of 24 x 24 x 24 voxels. This avoids the loss of the shape information when the voxels are too small (so that the object is larger than the grid) or when th voxels are too large (so that details are lost by aliasing).
- Voxel grid is subtracted by 0.5 and multiplied by 2, so that the input is in the rang (-1, 1).
- Implement a multiresolution VoxNet, where two networks with an identical architectures, each receiving occupancy grids at different resolutions: (0.1m)<sup>3</sup> and (0.2m)<sup>3</sup>. Connected by a softmax output layer.

## Results

#### Effect of Occupancy Grids

| Occupancy | Sydney F1 | NYUv2 Acc |
| --------- | --------- | --------- |
| Density   | **0.72**  | **0.71**  |
| Binary    | 0.71      | 0.69      |
| Hit       | 0.70      | 0.70      |

#### Sydney Object Dataset

| Method    | Avg F1    |
| --------- | --------- |
| UFL+SVM   | 0.67      |
| GFH+SVM   | 0.71      |
| MR-VoxNet | **0.73**  |

#### ModelNet Dataset

| Dataset    | ShapeNet  | VoxNet    |
| ---------- | --------- | --------- |
| ModelNet10 | 0.84      | **0.92**  |
| ModelNet40 | 0.77      | **0.83**  |

#### NYUv2 (Avg Acc)

| Dataset         | ShapeNet  | VoxNet    | VoxNet Hit |
| --------------- | --------- | --------- | ---------- |
| NYU             | 0.58      | **0.71**  | 0.70       |
| ModelNet10->NYU | 0.77      | **0.83**  | 0.25       |


# Resource
## Paper
https://www.ri.cmu.edu/pub_files/2015/9/voxnet_maturana_scherer_iros15.pdf

## Project Page
http://dimatura.net/research/voxnet/

## Source code
https://github.com/dimatura/voxnet

## Build upon
- Integration of data from other modalities (e.g. cameras).
- Application of method to other tasks such as semantic segmentation.

## Key Words
- Voxel
- CNN

## Software & Hardware
- C++
- Python
- Lasagne library
- Tesla K40 GPU (training: 6 to 12 hours)
