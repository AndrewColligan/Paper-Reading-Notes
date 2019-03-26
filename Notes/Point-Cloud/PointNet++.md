# Basic info
- Title: PointNet++: Deep Hierarchical Feature Learning on Point Sets in a Metric Space
- Author: Charles R. Qi Li Yi Hao Su Leonidas & J. Guibas
- Affiliation: Stanford University
- Publication status: 2017 Conference on Neural Information Processing Systems (NIPS)
- Short name: PointNet++
- Year: 2017

# Score
- Idea: 
- Usability: 
- Presentation: 
- Overall: 

# Contributions
## Problem addressed / Motivation
- Point clouds are captured by 3D scanners such as from autonomous vehicles.
- PointNet does not capture local structures induced by the metric space, points lives in, limiting its ability to recognise fine-grained patterns and generalise to complex scenes.
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


## Useful info / tips
- The partitioning of the point set has to produce common structures across partitions, so weights of local feature learners can be shared, as in the convolutional setting.

# Evaluation
## Dataset


## Metrics


## Results


# Resource
## Paper
https://arxiv.org/pdf/1706.02413.pdf

## Project page
http://stanford.edu/~rqi/pointnet2/

## Source code
https://github.com/charlesq34/pointnet2

## Dataset


## Other paper reading notes


## Others


## Questions


## Build upon


## Paper connections


## Software & Hardware

