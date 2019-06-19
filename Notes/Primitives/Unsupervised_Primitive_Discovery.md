# Basic info
- Title: Unsupervised Primitive Discovery for Improved 3D Generative Modeling
- Author: Salman H. Khan, Yulan Guo, Munawar Hayat & Nick Barnes
- Affiliation: Inception Institute of Artificial Intelligence, UAE; National University of Defense Technology, China; Australian National University, AU; Sun Yat-sen University, China; University of Canberra, AU
- Publication status: CVPR2019
- Short name: Unsupervised Primitive Discovery
- Year: 2019

# Score
- Idea: 
- Usability: 
- Presentation: 
- Overall: 

# Contributions
## Problem addressed / Motivation
- Often primitive learning requires primitive-level shape labellings for training.
- Some approaches rely on expensive category specific training procedures.
- Goal is to learn common recurring primitives in 3D shapes in an unsupervised manner.

## Idea / Observation / Contribution
- Propose a novel factorised generative model for 3D shape generation that sequentially transitions from coarse to fine scale shape generation.
- Introduce an unsupervised primitive discovery algorithm based on a higher-order **conditional random field (CRF)** model.

## Formulation / Solver / Implementation
- Unsupervised approach.
- Higher-order CFR model incorporates several physical and volumetric properties of primitives to identify a consistent shape description.
- Multi-view primitive discovery approach is used to discretise the 3D space without losing much shape information and allows a computationally efficient alternative to direct 3D primitive fitting.

<p align="center">
  <img src="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Imgs/Unsupervised_Primitive_Discovery_3.PNG" width=700>
</p>

## Useful info / tips
- As objective is to discover shared primitives among the various models, direct cuboid fitting in the original 3D space would lead to more instance specific and less category generalizable primitives.

# Evaluation
## Dataset


## Metrics

<p align="center">
  <img src="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Imgs/Unsupervised_Primitive_Discovery_1.PNG" width=700>
  <br/>
  <b>Primitive GAN Architecture</b>
  <br/>
  <br/>
    <img src="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Imgs/Unsupervised_Primitive_Discovery_2.PNG" width=700>
  <br/>
  <b>3D Shape GAN Architecture</b>
</p>

## Results


# Resource
## Paper


## Project page


## Source code


## Dataset


## Other paper reading notes


## Others


## Questions


## Build upon


## Paper connections


## Software & Hardware

