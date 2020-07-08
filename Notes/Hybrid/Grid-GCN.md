# Basic info
- Title: Grid-GCN for Fast and Scalable Point Cloud Learning
- Author: Qiangeng Xu, Xudong Sun, Cho-Ying Wu, Panqu Wang & Ulrich Neumann
- Affiliation: University of Southern California & Tusimple, Inc
- Publication status:  2020 IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)
- Short name: Grid-GCN
- Year: 2020

# Score
- Idea: 4
- Usability: 4
- Presentation: 4
- Overall: 4

# Contributions
## Problem addressed / Motivation
-	Graph convolutional networks (GCN) operating on point cloud data have shown greater performance by fully preserving the data granularity and exploiting point interrelation.  
-	Point-based networks often spend a lot of time on data structuring (e.g. Farthest Point Sampling (FPS) and neighbor points querying).
-	This limits speed and scalability.

## Idea / Observation / Contribution
-	Proposes a fast and scalable point cloud learning solution.
-	A novel data structuring strategy called Coverage-Aware Grid Query (CAGQ).
-	This leverages the efficiency of grid space, this improves spatial coverage while reducing time complexity.

## Formulation / Solver / Implementation
The model consists several GridConv layers to process the point data. 
Each layer consists of two stages: 
-	A data structuring stage that samples the representative centers and queries the neighboring points. 
-	A convolutional stage that builds a local graph on each point group and aggregates the information to the center. 

<p align="center">
  <img src="https://images.deepai.org/converted-papers/1912.02984/figures/GGCN.png" width = 500>
</p>

### Coverage-Aware Grid Query (CAGQ) 
This module samples M point groups from N points. Aims to effectively structure the point cloud and ease the process of center sampling and neighbor points querying.

**Process**:
-	Voxelise input space to a certain size (a)
-	Each point in the point cloud is mapped to a voxel index (a)
-	Only a certain number of points are stored in each voxel in (b) this is 3 as denoted by the yellow circles
-	Center voxels are subset of non-empty voxels (b)
-	For each center voxel, the voxel neighbors are defined as voxels within the neighborhood of a center voxel
-	The stored points inside these voxel neighbors are context points
-	CAGQ picks node points from context points 
-	The barycenter of node points in a group is calculated as the group center 
-	A barycenter is the center of mass of two or more orbiting bodies

<p align="center">
  <img src="https://images.deepai.org/converted-papers/1912.02984/figures/CAGQ/CAGQ.png" width = 500>
</p>

### Grid Context Aggregation (GCA) 
A graph convolution module to exploit point relationships. It performs grid context pooling to extract context features of the grid neighborhood. This benefits the edge relation computation without adding extra overhead.

**Process**:
- Construct a local graph G(V,E) where V consists of the group center and K node points provided by CAGQ. 
- Connect each node point to the group center.
- GCA projects a node point’s features f<sub>i</sub> to f ̃_<sub>i</sub>.
- Based on the edge relation between the node and the center, GCA calculates the contribution of f ̃_<sub>i</sub> and aggregates all these features as the feature f ̃_<sub>c</sub>.

**Coverage Weight**
- The number of points that have been aggregated to a node in previous layers. 
- Used to give more attention to the node points with more information from previous layers.

**Grid Context Pooling**
- In CAGQ, a group center is calculated as the barycenter of the node points.
- Proposes grid context pooling to extract context features f_cxt by pooling from all context points.
- This sufficiently covers the entire grid space of the local graph.


# Evaluation
## Dataset
-	ModelNet10
-	ModelNet40
-	ScanNet
-	S3DIS

## Metrics
| Sample Centers | RPS | FPS | RVS | CAS |
| -------------- | ----------- | ---------- | ---------- | ---------- |
|                | O(N)        | O(NlogN)   | O(N)       | O(N)       |
| Query Nodes    | Ball Query  | Cube Query | k-NN       | CAGQ k-NN  |
|                | O(MN)       | O(MK)      | O(MN)      | O(Mn<sub>v</sub> |

## Results
|                |             | ModelNet40  |            | ModelNet10   |          |              |
| Input (xyz)    |             | OA          | mAcc       | OA           | mAcc     | Latency (ms) |
| Grid-GCN       | 16x1024     | 93.1        | 91.3       | 97.5         | 97.4     | 42.2         |

# Resource
## Paper
https://arxiv.org/pdf/1912.02984.pdf

## Source code
https://github.com/ICpachong/Grid-GCN

## Paper connections
- Point cloud
- Voxels
- Graph convolutional networks

## Software & Hardware
- RTX 2080 GPU
