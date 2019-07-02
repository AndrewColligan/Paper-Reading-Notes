# Basic info
- Title: CAD Defeaturing Using Machine Learning
- Author: 
- Affiliation: 
- Publication status: 
- Short name: CAD Defeaturing Using ML
- Year: 2019

# Score
- Idea: 
- Usability: 
- Presentation: 
- Overall: 

# Contributions
## Problem addressed / Motivation
- Using machine learning for the defeaturing of CAD models for tetrahedral meshing.

## Idea / Observation / Contribution
- Using machine learning predictions of mesh quality for geometric features of a CAD model prior to meshing.
- This can be used to identify potential problems areas and improve meshing outcomes by presenting a prioritised list of suggested geometric operations to users.

## Formulation / Solver / Implementation
- **Ensemble of decision trees (EDT)** containing 75 trees with a maximum tree depth of 25.

## Useful info / tips
- Only capable of defeaturing individual parts.

# Evaluation
## Dataset
- 94 CAD models for GrabCAD

## Metrics
- Mesh quality metrics
  1. **Scaled Jacobian** - the minimum Jacobian at any of the four vertices of a tetrahedron divided by the lengths of its three adjacent edges.
  2. **In-Radius** - the radius of an inscribed sphere within a tetrahedra.
  3. **Deviation** - the distance from the centroid of a surface triangle to its closest point on the geometry.
  
- Locality of mesh metrics
  1. **Bounding box**
  2. **Local topology**


## Results


# Resource
## Paper


## Project page


## Source code


## Questions


