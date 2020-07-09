# Basic info
- Title: Deep Hierarchical Graph Convolution for Election Prediction from Geospatial Census Data
- Author: Mike Li, Elija Perrier & Chang Xu
- Affiliation: 
  1. Centre for Complex Systems, The University of Sydney, Sydney, Australia
  2. Centre for Quantum Software and Information, The University of Technology, Sydney, Australia
  3. UBTECH Sydney AI Centre, School of Computer Science, FEIT, University of Sydney, Australia
- Publication status: AAAI-19
- Short name: Hierarchical GCNN
- Year: 2019

# Score
- Idea: 
- Usability: 
- Presentation: 
- Overall: 

# Contributions
## Problem addressed / Motivation
- Geographic information systems (**GIS**) research used within social and physical sciences and used in the development of government policies.
- Application of deep learning on GIS datasets have been limited due to the complex and poorly structured nature of the data.
- Many current techniques ignore the geography of GIS data (including spatial boundaries, clustering effects and distance measures).

## Idea / Observation / Contribution
- Demonstrate the utility of GCNNs for GIS analysis via a *multi-graph hierarchical spatial-filter GCNN network model*.
- Used to predict election outcomes using socio-economic features.
- Enhanced results by connecting neighboring statistical regions into a planar graph and performing graph convolutions along these edges.
- Opposed to spectral filters, **spatial filters** are framed as polynomial functions of the usual adjacency matrix and learning occurs in the spatial domain.
- Since they act per node by construction, the localised interactions allow well-defined connections between graphs in a multi-graph content. Enabling the operation on the hieractical nature of GIS datasets.

<p align="center">
  <img src="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Imgs/Hierarchical_GCNN_Fig_1.PNG" width = 500>
</p>

## Formulation / Solver / Implementation
### Data
- Used Census data where populations are grouped into geospatial polygonal areas.
- The smallest area were the Statistical Area Level 1 (**SA1**) where Census socioeconomic data was available.
- **SA2**, **SA3** etc. are hierarchy successive clusters attributing to larger regional aggregations.
- A link between SA1 and SA2 nodes is constructed.

<p align="center">
  <img src="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Imgs/Hierarchical_GCNN_Fig_2.PNG" width = 500>
</p>

### Hierarchical GCNN
- Simply combining multi-level GIS graphs into one single large graph could become computationally intractable.
- Or lead to overfitting due to expanded parameterisation during training from the consolidation of adjacency matrices into an expanded adjacency relation.
- For GCNN GIS analysis, important to be able to run parallel GCNNs across networked but distinct graphs.
- This connection should control the information transmitted from one graph to another.
- For an SA1 graph of *n* nodes and SA2 graph of *m* nodes (*m*<*n*).
- SA1 adjacency matrix <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{A}^{_{1}}\in&space;\mathbb{R}^{^{n\times&space;n}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{A}^{_{1}}\in&space;\mathbb{R}^{^{n\times&space;n}}" title="\mathbf{A}^{_{1}}\in \mathbb{R}^{^{n\times n}}" /></a> and SA2 adjacency matrix <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{A}^{_{2}}\in&space;\mathbb{R}^{^{m\times&space;m}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{A}^{_{2}}\in&space;\mathbb{R}^{^{m\times&space;m}}" title="\mathbf{A}^{_{2}}\in \mathbb{R}^{^{m\times m}}" /></a>.
- Matrices <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{A}^{_{3}}\in&space;\mathbb{R}^{^{n\times&space;m}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{A}^{_{3}}\in&space;\mathbb{R}^{^{n\times&space;m}}" title="\mathbf{A}^{_{3}}\in \mathbb{R}^{^{n\times m}}" /></a> and <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{A}^{_{4}}\in&space;\mathbb{R}^{^{m\times&space;n}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{A}^{_{4}}\in&space;\mathbb{R}^{^{m\times&space;n}}" title="\mathbf{A}^{_{4}}\in \mathbb{R}^{^{m\times n}}" /></a> are linear operators that facilitate information-sharing between the different-dimensional feature spaces of each level.
<p align="center"><a href="https://www.codecogs.com/eqnedit.php?latex=Embedding&space;-&space;\mathbf{A}^{{_{3}}^{(n\times&space;m)}}:\mathbb{R}^{^{m\times&space;1}}\rightarrow&space;\mathbb{R}^{n\times&space;1},&space;\:\:&space;\:&space;\:&space;\:&space;\:&space;\mathbf{V}^{^{(m\times&space;1)}}&space;\mapsto&space;\boldsymbol{\mathbf{V}&space;}^{(n\times&space;1)}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?Embedding&space;-&space;\mathbf{A}^{{_{3}}^{(n\times&space;m)}}:\mathbb{R}^{^{m\times&space;1}}\rightarrow&space;\mathbb{R}^{n\times&space;1},&space;\:\:&space;\:&space;\:&space;\:&space;\:&space;\mathbf{V}^{^{(m\times&space;1)}}&space;\mapsto&space;\boldsymbol{\mathbf{V}&space;}^{(n\times&space;1)}" title="Embedding - \mathbf{A}^{{_{3}}^{(n\times m)}}:\mathbb{R}^{^{m\times 1}}\rightarrow \mathbb{R}^{n\times 1}, \:\: \: \: \: \: \mathbf{V}^{^{(m\times 1)}} \mapsto \boldsymbol{\mathbf{V} }^{(n\times 1)}" /></a></p>

- The embedding transfers information from the SA2 level graph to the SA1 level graph by acting on SA2 vertex vectors <a href="https://www.codecogs.com/eqnedit.php?latex=\boldsymbol{\mathbf{V}&space;}^{(m\times&space;1)}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\boldsymbol{\mathbf{V}&space;}^{(m\times&space;1)}" title="\boldsymbol{\mathbf{V} }^{(m\times 1)}" /></a> (one for each SA1 feature.

<p align="center"><a href="https://www.codecogs.com/eqnedit.php?latex=Projection&space;-&space;\mathbf{A}^{{_{4}}^{(m\times&space;n)}}:\mathbb{R}^{^{n\times&space;1}}\rightarrow&space;\mathbb{R}^{m\times&space;1},&space;\:\:&space;\:&space;\:&space;\:&space;\:&space;\mathbf{V}^{^{(n\times&space;1)}}&space;\mapsto&space;\boldsymbol{\mathbf{V}&space;}^{(m\times&space;1)}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?Projection&space;-&space;\mathbf{A}^{{_{4}}^{(m\times&space;n)}}:\mathbb{R}^{^{n\times&space;1}}\rightarrow&space;\mathbb{R}^{m\times&space;1},&space;\:\:&space;\:&space;\:&space;\:&space;\:&space;\mathbf{V}^{^{(n\times&space;1)}}&space;\mapsto&space;\boldsymbol{\mathbf{V}&space;}^{(m\times&space;1)}" title="Projection - \mathbf{A}^{{_{4}}^{(m\times n)}}:\mathbb{R}^{^{n\times 1}}\rightarrow \mathbb{R}^{m\times 1}, \:\: \: \: \: \: \mathbf{V}^{^{(n\times 1)}} \mapsto \boldsymbol{\mathbf{V} }^{(m\times 1)}" /></a></p>

- The projection transfers information from the SA1 to SA2 level by acting on SA1 vertex vectors <a href="https://www.codecogs.com/eqnedit.php?latex=\boldsymbol{\mathbf{V}&space;}^{(n\times&space;1)}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\boldsymbol{\mathbf{V}&space;}^{(n\times&space;1)}" title="\boldsymbol{\mathbf{V} }^{(n\times 1)}" /></a> (one for each SA2 feature).
- Filter-learning is conducted on both levels separately using a combination of graph convolution and graph pool embeddings layers [(Such et al, 2017)](https://arxiv.org/abs/1703.00792).

<p align="center">
  <img src="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Imgs/Hierarchical_GCNN_Fig_3.PNG" width = 400>
</p>

# Evaluation
## Dataset


## Metrics


## Results
<p align="center">
  <img src="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Imgs/Hierarchical_GCNN_Tab_1.PNG" width = 800>
</p>

# Resource
## Paper
https://www.aaai.org/ojs/index.php/AAAI/article/view/3841

## Source code
https://github.com/mili7522/Hierarchical-GCNN

## Questions


## Build upon


## Paper connections
- Hierarchical Graph
- Graph Neural Networks (GNN)
- Graph Convolutional Neural Networks (GCNN)

## Software & Hardware


## Terms

