# Basic info
- Title: PointNet++: Deep Hierarchical Feature Learning on Point Sets in a Metric Space
- Author: Charles R. Qi Li Yi Hao Su Leonidas & J. Guibas
- Affiliation: Stanford University
- Publication status: 2017 Conference on Neural Information Processing Systems (NIPS)
- Short name: PointNet++
- Year: 2017

# Score
- Idea: 5
- Usability: 5
- Presentation: 5
- Overall: 5

# Contributions
## Problem addressed / Motivation
- Point clouds are captured by 3D scanners, such as for autonomous vehicles.
- PointNet does not capture local structures induced by the metric space, where the points lives in. This limits its ability to recognise fine-grained patterns and generalise to complex scenes.
- How to generate the partitioning of the point set?
- How to abstract sets of points or local features through a local feature learner?

## Idea / Observation / Contribution
- A hierarchical neural network to process a set of points sampled in a metric space in a hierarchical fashion.
- The set of points are partitioned into overlapping local regions by the distance metric of the underlying space.
- Similar to CNNs, they extract local features capturing fine geometric structures from small neighbourhoods; such local features are further grouped into larger units and processed to produce higher level features.
- This process is repeated until they obtain the features of the whole point set.

<p align="center">
  <img src="http://stanford.edu/~rqi/pointnet2/images/pnpp.jpg" width=500>
</p>

## Formulation / Solver / Implementation
- The architecture is composed of multiple components that aggregate local information and pass it along to the next step.
- Since point clouds are unordered, the aggregation steps cannot depend on the order of the input.
- Therefore, a *symmetric* function (*f(x,y,z) = max(x,y,z)*) is used, where for each tiny group of points, after a few initial transformations there is a max operation that combines everything.
- There are a number of stages in the architecture, but each part has a well-defined goal.
- Starting from the entire point cloud, points are grouped into some number of clusters, and condensed into a single point that carries new information. In addition to its *d* spatial coordinates, each point also carries *C* pieces of information.
- This process continues, taking the new points and grouping them into more clusters.
- Depending on the problem, the process then reverses itself and tries to build back the original structure.
- Especially when we would like to classify each original point, the network has a series of interpolationg steps to go from one point to a group.
- These steps all rely on utilising the distance function.
- The interpolation step uses an inverse distance weighted average.

## Useful info / tips
- The partitioning of the point set has to produce common structures across partitions, so weights of local feature learners can be shared, as in the convolutional setting.

# Evaluation
## Dataset
- ModelNet40
- MNIST
- SHREC15
- ScanNet

## Metrics
- Performed on Euclidean and non-Euclidean metric space.
- Ball query used instead of kNN for grouping layer.

## Results

### ModelNet40 Shape Classification

| Method                   | Input | Accuracy (%) |
| ------------------------ | ----- | ------------ |
| Subvolume                | vox   | 89.2         |
| MVCNN                    | img   | 90.1         |
| PointNet                 | pc    | 87.2         |
| PointNet++               | pc    | 90.7         |
| PointNet++ (with normal) | pc    | **91.9**     |

# Resource
## Paper
https://arxiv.org/pdf/1706.02413.pdf

## Project page
http://stanford.edu/~rqi/pointnet2/

## Source code
https://github.com/charlesq34/pointnet2

## Build upon
- Accelerate inference speed of the network especially for multi-scale grouping (MSG)  and multi-resolution grouping (MRG) layers by sharing more computation in each local regions.
- Find applications in higher dimensional metric spaces where CNN based method would be computationally unfeasible while this method would scale well.

## Paper connections
- Point Cloud
- Non-CNN based

## Software & Hardware

