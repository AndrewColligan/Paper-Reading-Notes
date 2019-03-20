# Basic info
- Title: Geodesic Convolutional Neural Networks on Riemannian Manifolds
- Author: Jonathan Masci, Davide Boscaini, Michael M. Bronstein, Pierre Vandergheynst
- Affiliation: USI, Lugano, Switzerland & EPFL, Lausanne, Switzerland
- Publication status: 2015 IEEE International Conference on Computer Vision Workshop (ICCVW)
- Short name: GCNN
- Year: 2015

# Score
- Idea: 5
- Usability: 4
- Presentation: 3
- Overall: 4

# Contributions
## Problem addressed / Motivation
- Feature descriptors are tools in shape analysis. 
- A local feature descriptor assigns to each point on th shape a vector in some multi-dimensional descriptor space representing the local structure of the shape around that point.
- Method of learning the local descriptors by CNN.

## Idea / Observation / Contribution
- Propose Geodesic CNN (GCNN), an extension of the CNN paradigm to **non_Euclidean maniflods** based on *local geodesic system of coordinates* that are analogous to **patches** in images.
- Compare to other work on non-Euclidean CNNs, their model is generalisable (i.e. it can be trained on one set of shapes and then applied to another one), local, and allows for the capture of **anisotropic** structures.
- Show that HKS, WKS, optimal spectral descriptors and intrinsic shape context can be obtained as particular configurations of GCNN. Therefore, apporach is a generalisation fo previous popular descriptors.
- Can be applied to a wide range of problems, including: the construction of shape descriptors, retrieval and correspondence.

<p align="center">
  <img src = "https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Imgs/gcnn2.png" width=500>
</p>

## Formulation / Solver / Implementation
- Model the 3D shape as a connected smooth compact 2D manifold (surface).
- Spectral descriptors: heat kernel signature (HKS), wave kernel signature (WKS) and optimal spectral descriptors (OSD).
- Geodesic convolution (GC), where a filter is applied on the patches. The filter can be rotated.
- On triangular meshes, a discrete local system of geodesic polar coordinates has angular and radial bins.
- Starting with a vertex, they first partition the l-ring by rays into equi-angular bins, aligning the first ray with one of the edges.
- Next, they propagate the rays into adjacent triangles using an unfolding procedure resembling one used in, producing poly-lines that form the angular bins.
- Radial bins are created as level sets of the geodesic distance function computed using fast marching.
- Convolutions are performed by sliding a window over the manifold, and local geodesic co-ordinates are used in place of image *patches*.

## Useful info / tips
- Spectral shape analysis relies on the spectrum (eigenvalues and/or eigenfunctions) of the Laplace–Beltrami operator to compare and analyze geometric shapes. Since the spectrum of the Laplace–Beltrami operator is invariant under isometries, it is well suited for the analysis or retrieval of non-rigid shapes, i.e. bendable objects such as humans, animals, plants, etc.
- The Laplace–Beltrami operator is involved in many important differential equations, such as the heat equation and the wave equation. It can be defined on a Riemannian manifold as the divergence of the gradient of a real-valued function f.
- The spectral decomposition of the graph Laplacian associated with complex shapes (see Discrete Laplace operator) provides eigenfunctions (modes) which are invariant to isometries. Each vertex on the shape could be uniquely represented with a combinations of the eigenmodal values at each point, sometimes called spectral coordinates.
- Spectral matching consists of establishing the point correspondences by pairing vertices on different shapes that have the most similar spectral coordinates. 

<p align="center">
  <img src = "https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Imgs/gcnn.png">
</p>

# Evaluation
## Dataset
- FAUST
- TOSCA

## Metrics
- **Siamese network** configuration, composed of two identical copies of the same GCSNN model sharing the same parameterization and fed by pairs of knowingly similar or dissimilar samples, and minimise the *siamese loss*.
- Quantitative descriptor evaluation was done using three criteria:
  1. Cumulative match characteristic (CMC): evaluates the probability of a correct correspondence among the *k* nearest neighbours in the descriptor space.
  2. Receiver operator characteristic (ROC): measures the percentage of positives and negative pairs falling below various thresholds of their distance in the descriptor space.
  3. Princeton protocol: counting the percentage of nearest-neighbour matches that are at most r-geodesically distant from the groundtruth correspondence.

## Results
- Performed better than other previous shape descriptors.

# Resource
## Paper
https://arxiv.org/abs/1501.06297

## Project page
https://www.inf.usi.ch/phd/boscaini/sections/publications.html

## Source code
https://github.com/jonathanmasci/ShapeNet_data_preparation_toolbox

## Questions
- Can this be used on Attribute Adjacency Graphs (AAG).

## Build upon
- Could be used for point cloud.

## Paper connections
- Non-Euclidean Manifolds
- Geodesic CNN

## Software & Hardware
- Theano
