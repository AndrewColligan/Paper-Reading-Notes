# Basic info
- Title: Hierarchical Graph Representation Learning with Differentiable Pooling
- Author: Rex Ying, Jiaxuan You, Christopher Morris, Xiang Ren, William L. Hamilton & Jure Leskovec
- Affiliation: Stanford University, TU Dortmund University & University of Southern California
- Publication status: NIPS 2018
- Short name: DiffPool
- Year: 2018

# Score
- Idea: 
- Usability: 
- Presentation: 5
- Overall: 

# Contributions
## Problem addressed / Motivation
- Current GNN methods do not learn **hierarchical** representations of graphs.
- This is very problematic for graph classification where the goal is to predict the label associated with an entire graph.
- Normally, embeddings are generated for all the nodes in the graph and then the node embeddings are *globally pooled* together. Not using hierarchical structure.
- Example: A organic molecule involve local molecular structure (e.g. individual atoms and their direct bonds) and coarse-grained structure of the molecular graph (e.g. groups of atoms and bonds representing functional units in a molecule).

## Idea / Observation / Contribution
- Propose DIFFPOOL that is a differentiable graph pooling module.
- This can generate hierarchical representations of graphs and can be combined with various GNN architectures in an *end-to-end* fashion.
- Learns a differentiable [soft cluster assignment](#Terms) for nodes at each layer of a deep GNN. 
- This maps nodes to a set of clusters, which form the coarsened input for the next GNN layer. 

<p align="center">
  <img src="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Imgs/diffpool.png" width = 700>
</p>

## Formulation / Solver / Implementation
- At each hierarchical layer, a GNN model is run to obtain embeddings of nodes. 
- The learnt embeddings are used to cluster nodes together.
- Another GNN layer is then run on the coarser graph.
- This process is repeated for each layer of the network.
- The final output representation is used to classify the graph.


# Evaluation
## Dataset
- ENZYMES
- PROTEINS
- D&D
- REDDIT-MULTI-12K
- COLLAB

## Metrics
- Built upon [GRAPHSAGE](https://cs.stanford.edu/people/jure/pubs/graphsage-nips17.pdf) architecture.
- When using 2 DIFFPOOL layer architecture, number of clusters is set to 25% of the number of nodes before applying DIFFPOOL.
- When using 1 DIFFPOOL layer architecture, number of clusters is set to 10% of the number of nodes before applying DIFFPOOL.
- Batch normalization.
- L<sub>2</sub> normalization.
- 3,000 epochs with early stopping.

## Results
<p align="center">
  <img src="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Imgs/diffpool_results.PNG" width = 700>
</p>


# Resource
## Paper
https://arxiv.org/abs/1806.08804

## Source code


## Questions


## Build upon


## Paper connections
- Hierarchical Graph
- Graph Neural Networks

## Software & Hardware


## Terms
**Hard Clustering** 
- Grouping data items such that each item is only assigned to one cluster.

**Soft Cluster**
- Grouping the data items such that an item can exist in multiple clusters. 