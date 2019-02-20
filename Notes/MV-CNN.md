# Basic info
- Title: Multi-View Convolutional Neural Networks for 3D Shape Recognition
- Author: Hang Su, Subhransu Maji, Evangelos Kalogerakis, Erik Learned-Miller
- Affiliation: University of Massachusetts, Amherst
- Publication status: 
- Short name: MV-CNN
- Year: 2015

# Score
- Idea: 
- Usability: 
- Presentation: 
- Overall: 

# Contributions
## Problem addressed / Motivation
- Emersion of more 3D data.
- Use 2D due to its relative efficiency over 3D representations.
- No need to reduce resolution, to train in reasonable time.
- Leverage advances in image descriptors and large image databases to pre-train CNN architecture.

## Idea / Observation / Contribution
- MV-CNN related to **jittering** where transformed copies of the data are added during training to learn invariances to transformations; such as rotation or translation.
- CNN learns to combine the views instead of averaging, and can use the more informative views of the object for prediction while ignoring others.

<img src='http://vis-www.cs.umass.edu/mvcnn/images/mvcnn.png' alt="MV-CNN Network" width=600 align="middle">

## Formulation / Solver / Implementation
- All parameters of CNN are learned discriminatively to produce a single compact descriptor for 3D shape from the multiple views.
- Phong reflection model used to generate rendered views of polygon meshes, which are rendered under a perspective projection and the pixel colour is found by interpolating reflected intensity of polygon vertices.
- **1st camera setup** - all input shapes assumed to be orientated upright along a consistent axis. 12 rendered views from 12 cameras every 30 degrees.
- **2nd camera setup** - 20 virtual cmeras at 20 vertices of an icosahedron enclosing the shape, as don't know the orientation. Generate 4 rendered views from each camera, using 0, 90. 180, 270 degrees rotation to yield 80 views.
- MVCNN optimised for classification not retrieval. Instead of learning different objective function, learn **Mahalanobis metric W**.

# Evaluation
## Dataset
- ModelNet

## Metrics
- Compared against 3DShapeNet, Spherical Harmonics descriptor (SPH), LightField descriptor (LFD) and Fisher vectors extracted on the same rendered views of the shapes used as input to our networks. 

## Results
- 12 View Classification Accuracy = 88.6%.
- 12 View Retrieval = 62.8%.
- 80 View Classification Accuracy = 89.9%.
- 80 Views Retrieval = 70.1%.

# Resource
## Project page
http://vis-www.cs.umass.edu/mvcnn/

## Source code
https://github.com/WeiTang114/MVCNN-TensorFlow

# Key Words
- CNN
- Multi-View
