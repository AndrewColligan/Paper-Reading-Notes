# Basic info
- Title: Orientation-boosted Voxel Nets for 3D Object Recognition
- Author: Nima Sedaghat, Mohammadreza Zolfaghari, Ehsan Amiri & Thomas Brox
- Affiliation: Computer Vision Group, University of Freiburg, Germany
- Publication status: British Machine Vision Conference BMVC 2017
- Short name: ORION
- Year: 2017

# Score
- Idea: 3
- Usability: 3
- Presentation: 3
- Overall: 3

# Contributions
## Problem addressed / Motivation
- Object orientation plays an important role in 3D recognition by inducing different features under rotation.
- This requires a network to learn the underlying concepts, such as object pose, that generalise to variations in the data.
- Often, the network does not learn the full underlying concept, but some representation that only partially generalises to new data.

## Idea / Observation / Contribution
- In this paper, orientation classification is added as an auxiliary task to the 3D classification network. 
- The network is forced to produce the correct orientation during training and is shown to increase classification accuracy, by an explicit loss on the orientation.
- Also apply classifier in a 3D detection scenerio using a simple 3D sliding box approach.
- Here, the orientation estimation is no longer just an auxiliary task, but also determines the orientation of the box, which largely reduces the runtime of the 3D detector.

<p align="center">
  <img src="https://camo.githubusercontent.com/5176a16222b16692057c62b09a92b35a1dcd161c/68747470733a2f2f6c6d622e696e666f726d6174696b2e756e692d66726569627572672e64652f5075626c69636174696f6e732f323031372f535a423137612f7465617365725f772e706e67" width=700>
</p>

## Formulation / Solver / Implementation
- Core network architecture is based on VoxNet, allowing for direct comparisons.
- Only consider rotation around the z-axis (azimuth), as the most varying component of orientation in practical applications.
- Do not put the same orientations from different object classes into the same orientation class, because they do not seek to extract any information from the absolute pose of the objects.
- Sharing the orientation output for all classes would make the network learn features shared among classes to determine the orientation, they want to leverage the orientation estimation as an auxiliary task to improve on object classification.
- During the test phase, multiple rotations are feed to the network and obtain a final consensus on the class label based on the votes they obtain from each interence pass.


## Useful info / tips
- You can have binary and continuous-valued occupancy grids.

# Evaluation
## Dataset
- Sydney Urban Objects (LiDAR/Pointcloud).
- NYUv2 (Kinect/RGBD).
- ModelNet (Synthetic/CAD).
- KITTI (LiDAR/Pointcloud).

## Metrics
- Voxel grid (32x32x32).
- F1 score used for Sydney Urban Objects dataset, average accuracy for others.

## Results

| Conv | Param | Sydney | NYUv2 | ModelNet10 |
| ---- | ----- | ------ | ----- | ---------- |
| 2    | 910K  | 77.8   | 75.4  | 93.8       |
| 4    | 4M    | 77.5   | 75.5  | 93.9       |

- Experimented with a deeper net, but found networks starts to overfit on the smaller datasets.
- Also annotated aligmments to ModelNet40, as it does not come with these annotations. Achieved highest accuracy of **89.7%**. This was achieved by the 4 conv layer network.
- They also found that by adding batch normalisation, there was a consistent improvement in results, due to batch normalisation causing the error from the second task to propagate deeper back into the network.
- Found that ORION managed to spread the contributions over different filters for different orientations.

# Resource
## Paper
https://arxiv.org/abs/1604.03351

## Source code
https://github.com/lmb-freiburg/orion

## Paper connections
- Voxel
- 3D CNN
