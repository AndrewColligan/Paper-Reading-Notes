# Basic info
- Title: Learning Shape Abstractions by Assembling Volumetric Primitives
- Author: Shubham Tulsiani, Hao Su, Leonidas J. Guibas, Alexei A. Efros, Jitendra Malik
- Affiliation: University of California Berkeley & Stanford University
- Publication status: CVPR
- Short name: LSAAVP
- Year: 2017

# Score
- Idea: 4
- Usability: 4
- Presentation:4 
- Overall: 4

# Contributions
## Problem addressed / Motivation
- *Parsimony of description* where an object can be described by relatively few generalised cylinders, each of which in turn require only a few parameters.
- Method of describing complex structures in terms of simpler underlying structures.

<p align="center">
    <img src="https://camo.githubusercontent.com/453106e3025f7bc61ca00629185699ac6e502430/68747470733a2f2f736875626874756c732e6769746875622e696f2f766f6c756d65747269635072696d6974697665732f7265736f75726365732f696d616765732f7465617365722e706e67" width=800>
</p>

## Idea / Observation / Contribution
- Explain objects with volumetric primitives using modern tools of unsupervised learning and convolutional neural networks (CNNs).
- The simpliest primitive is chosen: **rigidly transformed cuboids**.
- Show how deep networks can be trained to assemble arbitrary 3D objects out of them (at some level of approximation).
- Using 3D data as primitives is *parsimonious*, with a small number of parameters compared to voxels & meshes.

## Formulation / Solver / Implementation
- Approach outputs a consistent indexed set of primitives.
- Similar to shape and scene based methods, their framework can automatically discovers consistent components and understand the structure of the data, by virtue of learning to generate parimonious explanations.
- Similar to deep generative models like GANs, their work uses similar principles of learning component based explanations of complex shapes where the components are interpretable simple 3D primitives.
- No direct supervision, but the quality of the predicted primitive configuration is checked by matching the assembled object to the target object using *distance fields*.
- Allows variable number of primitves by not only predicting the shape and transformation of each primitive, but also the probability of its existence.
- CNN

# Evaluation
## Dataset
- ShapeNet - airplane and chair categories.
- 100 models of four-legged animals.
- Shape COSEG

## Metrics
- Each primitive is coded as a tuple (z: shape in a canonical frame, q: rotation, t: translation).
- Two loses that are optimised together, to ensure that the assembled shape tries to be maximally consistent with the target object:
    1. **Converage Loss**: tries to enforce that the object is subsumed by the predicted assembled shape.
    2. **Consistency Loss**: enforces the other direction that the object subsumes the predicted shape.
- For the variable number of primitives, the primitive shape *z<sub>m</sub>* is factored into two components - (*z<sup>s</sup><sub>m</sub>, z<sup>e</sup><sub>m</sub>*). Here *z<sup>s</sup><sub>m</sub>* represents the primitive dimensions (e.g. cuboid, height, width, depth) as before and *z<sup>e</sup><sub>m</sub>* is a binary variable which denotes if the primitive actaully exists.
- Gradients computed using **reinforce** algorithm, which gives positive feedback if the overall error is low (reward is high). A small *parsimony reward* is given reward fewer predicted primitives.
- Voxel grid of size: 32<sup>3</sup>.
 

## Results
- Mean accuracy: 89.0%.

# Resource
## Paper
https://arxiv.org/abs/1612.00404

## Source code
https://github.com/shubhtuls/volumetricPrimitives

## Build upon
- Wider catalogue if basic parametrised primitives.
- Use prediction of variable number of primitives for CSGNet.

## Paper connections
- CNN
