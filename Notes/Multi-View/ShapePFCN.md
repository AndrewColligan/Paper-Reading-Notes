# Basic info
- Title: 3D Shape Segmentation with Projective Convolutional Networks
- Author: Evangelos Kalogerakis,  Melinos Averkiou, Subhransu Maji & Siddhartha Chaudhuri
- Affiliation: University of Massachusetts Amherst, University of Cyprus & IIT Bombay
- Publication status: 2017 IEEE Conference on Computer Vision and Pattern Recognition
- Short name: ShapePFCN
- Year: 2017

# Score
- Idea: 
- Usability: 
- Presentation: 
- Overall: 

# Contributions
## Problem addressed / Motivation
- There has been significant advances in analysing colour images, especially through deep networks, existing semantic reasoning techniques for 3D geometric shape data mostly rely on heuristic processing stages and hand-tuned geometric descriptors.

## Idea / Observation / Contribution
- Deep architecture combining **view-based FCN** & **surface-based CRF**.
- **Multi-scale view selection** to avoid loss of surface information.
- Transfer learning from massive image datasets.
- Robust to geometric representation artifacts.

<p align="center">
	<img src="https://people.cs.umass.edu/~kalo/papers/shapepfcn/teaser.jpg">
</p>

## Formulation / Solver / Implementation
- Architecture 

## Useful info / tips
- View must be selected such that they together cover the shape surface as much as possible and minimise occlusions.
- Shape parts can be visible in more than one view, thus their method must effectively consolidate information across multiple views.
- Must guarantee that the segmentation is complete and coherent. This means all the surface area, including any heavily occluded portions, should be labeled, and neighbouring surface areas should likely have the same label unless separated by a strong boundary feature.
- **Surface-based Conditional Random Field (CRF)** layer promotes consistent labeling of the entire surface and resolve missing surface information in the view representation.

# Evaluation
## Dataset


## Metrics
- Input is a raw polygon mesh.

## Results


# Resource
## Paper
https://arxiv.org/pdf/1612.02808.pdf

## Project page
https://people.cs.umass.edu/~kalo/papers/shapepfcn/

## Source code
https://github.com/kalov/ShapePFCN

## Dataset

## Other paper reading notes

## Others

## Questions


## Build upon


## Paper connections
- Multi-view
- FCN
- CRF

## Software & Hardware
