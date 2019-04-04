# Basic info
- Title: MeshNet: Mesh Neural Network for 3D Shape Representation
- Author: Yutong Feng, Yifan Feng, Haoxuan You, Xibin Zhao1 & Yue Gao1
- Affiliation: BNRist, KLISS, School of Software, Tsinghua University, China & School of Information Science and Engineering, Xiamen University.
- Publication status: 2019 AAAI 
- Short name: MeshNet
- Year: 2019

# Score
- Idea: 5
- Usability: 5
- Presentation: 5
- Overall: 5

# Contributions
## Problem addressed / Motivation
- Learn from mesh data of 3D shapes, which is traditionally used in computer graphics for rendering and storing 3D models, because it porvides an approximation of the smooth surfaces of objects and simplifies the rendering process.
- It has a stronger ability to describe 3D shapes than voxels or point clouds etc.
- However, there are several problems that make it difficult to use deep learning networks on this type of data.
- There is **complexity** in the fact that mesh consists of multiple elements, and different types of connections may be defined among them.
- The data also has **irregularity**, which is a problem for mesh data processing, which indicates that the number of elements in the mesh may vary dramatically among 3D shapes, and permutations of them are arbitary.

## Idea / Observation / Contribution
- Propose a neural network using mesh for 3D shape representation and design blocks for capturing and aggregating features of polygon faces in 3D shapes.
- Conduct experiments to evaluate the performance of the proposed method, and the experimental results show that the proposed method performs well on 3D shape classification and retrieval tasks.

<p align="center">
  <img src="https://camo.githubusercontent.com/2d53e9921fbb6497922c2b452ecd62b0ee14cead/687474703a2f2f7777772e67616f7975652e6f72672f656e5f7473696e676875612f72657372632f6d6573686e65742e6a7067" width=700>
</p>

## Formulation / Solver / Implementation
- Faces are regarded as the unit and connections between faces sharing common edges are defined, which enables them to solve the complexity and irregularity problem with **per-face processes** and a **symmetry function**.
- Feature of faces is split into spatial and structural features, which helps to capture features more explicity. Where the network architecture, with two blocks named spatial and structural descriptions for learning the initial features, and a mesh convolution block for aggregating neighbouring features.
- The mesh data is transformed intp a list of faces. For each face, the initial values are defined, ehich are divided into two parts:
  - **Face Information**
    - **Center**: coordinates of the center point.
    - **Corner**: vector from the center point to three vertices.
    - **Normal**: the unit normal vector.
  - **Neighbouring Information**
    - **Neighbour Index**: Indexes of the connected faces (filled with the index of itself if the face connects with less than three faces).
- **Spatial feature** is expected to be relevant to the spatial position of faces.
- **Structural feature** is relevant to the shape information and lcoal structures.

## Useful info / tips
- Mesh does not have as much loss of natural information.
- In mesh data, there are explicit connection relationships to show the local structure clearly.

# Evaluation
## Dataset
- ModelNet40

## Metrics
- Only consider triangular faces.
- Concatenation is used instead of average pooling and max pooling, because it keeps the original activation and leaves space for the network to combine neighbouring features.
- Mesh data simplified to no more than *1,024 faces*, translated to geometric center, and normalised into a unit sphere.
- The normal vector and indexes of connected faces for each face are calculated.
- Since the number of faces vaires among the models, they randomly fill the list of faces to the length of 1024 with existing faces for batch training.

## Results
- It is shown that the accuracy is absolutely irrelevant to the number of faces and shows no downtrend with the decrease of it, which proves the robustness of MeshNet to the number of faces.
- MeshNet shows comparable effectiveness with methods based on point cloud in both time and space complexity, leaving enough space for future development.
- In the visualisation of the result, it can be seen that faces in similar types of areas, such as flat surfaces and steep slopes, tend to have similar features, regardless of their own shapes and sizes.
- Accuracy of **91.9%** on ModelNet with an mAP of **81.9%**.

# Resource
## Paper
https://www.aaai.org/Papers/AAAI/2019/AAAI-FengYutong.2101.pdf

## Source code
https://www.aaai.org/Papers/AAAI/2019/AAAI-FengYutong.2101.pdf

## Questions
- Could this be used in current research? Probably best for feature recognition.

## Paper connections
- Mesh

## Software & Hardware
- Pytorch
