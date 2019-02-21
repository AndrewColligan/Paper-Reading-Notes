# Basic info
- Title: PointNet: Deep Learning on Point Sets for 3D Classification and Segmentation
- Author: Charles R. Qi, Hao Su, Kaichun Mo, Leonidas J. Guibas
- Affiliation: Stanford University
- Publication status: 2017 IEEE Conference on Computer Vision and Pattern Recognition
- Short name: PointNet
- Year: 2017

# Score
- Idea: 5 
- Usability: 5
- Presentation: 3
- Overall: 4

# Contributions
## Problem addressed / Motivation
- Input data formats for NN architectures are regular.
- Point clouds or meshes are irregular format, therefore are normally converted in different representation.
- This makes data unnecessarily voluminous, which introduces quantization artifacts that obscure natural invariances of data.

## Idea / Observation / Contribution
- Network that directly takes unorderd point clouds as input and outputs either class labels for entire input or per point segment/part labels for each point of the input.
- Network learns a set of optimisation functions that select interesting or informative points of the point cloud and encode the reason for their selection.

<img src="https://github.com/charlesq34/pointnet/raw/master/doc/teaser.png" alt="PointNet" width="600" align="middle">

## Formulation / Solver / Implementation
- PointNet must respect the fact that a point cloud is just a set of points and therefore invariant to permutations of its members, necessitating certain symmetrisations in the net computation.
- Invariances to rigid motions need to be considered.
- Can apply rigid or affine transformations to input format easily, as each point transforms independently. Therefore, a data-dependent spatial transformer network can be added to canonicalise the data before PointNet processes them.
- Learns to summarise an input point cloud by a sparse set of key points, roughly correspons to the skeleton of objects according to visualisation.
- Each point Pi is a vector of its (x, y, z) coordinate plus extra feature channels such a colours, normal etc.
- To make the model invariant to input permutations, a simple symmetric function is used to aggregate the information from each point.
- Segmentation requires a combination of local and global knowledge, therefore, after computing the global point cloud feature vector, they feed back to per point features and extracted new per point features based on combined point features of per point and global features.

## Useful info / tips
- Point clouds are simple and unified structures that avoid the combinatorial irregularities and complexities of meshes, and thus are easier to learn.
- Each point represented by 3 coordinates (x, y, z), however additional dimensions can be added by computing normals and other local or global features.

# Evaluation
## Dataset
- ModelNet40
- ShapeNet

## Metrics
- Experiments divided into four parts:
  1. Show PointNet can be applied to multiple 3D recogntion tasks.
  2. Provide detailed experimetns to validate network design.
  3. Visualise what the network learns.
  4. Analysis time and space complexity.
- MLP used as network.

## Results
- ModelNet overall accuracy: 89.2%.
- ShapeNet mean accuracy: 83.7%.

# Resource
## Project page
http://stanford.edu/~rqi/pointnet/

## Source code
https://github.com/charlesq34/pointnet

# Key Words
- Point cloud 
- MLP

# Equipment & Software
- Python 2.7
-Tensorflow 1.01
