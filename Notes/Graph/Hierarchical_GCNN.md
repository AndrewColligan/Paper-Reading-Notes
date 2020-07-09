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

# Evaluation
## Dataset


## Metrics


## Results

# Resource
## Paper
https://www.aaai.org/ojs/index.php/AAAI/article/view/3841

## Source code


## Questions


## Build upon


## Paper connections
- Hierarchical Graph
- Graph Neural Networks (GNN)
- Graph Convolutional Neural Networks (GCNN)

## Software & Hardware


## Terms

