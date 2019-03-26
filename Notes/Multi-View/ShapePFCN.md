# Basic info
- Title: 3D Shape Segmentation with Projective Convolutional Networks
- Author: Evangelos Kalogerakis,  Melinos Averkiou, Subhransu Maji & Siddhartha Chaudhuri
- Affiliation: University of Massachusetts Amherst, University of Cyprus & IIT Bombay
- Publication status: 2017 IEEE Conference on Computer Vision and Pattern Recognition
- Short name: ShapePFCN
- Year: 2017

# Score
- Idea: 3
- Usability: 2
- Presentation: 4
- Overall: 3

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
- Architecture takes as input a set of images from multiple views optimised for maximal surface coverage.
- Extracts part-based confidence maps through pre-trained image processing layers.
- Combines and projects these maps onto the surface through a projection layer.
- Incorporates a surface-based Condition Random Field (CRF) that favours coherent labeling of the input surface.
- Whole network is trained end-to-end.

## Useful info / tips
- View must be selected such that they together cover the shape surface as much as possible and minimise occlusions.
- Shape parts can be visible in more than one view, thus their method must effectively consolidate information across multiple views.
- Must guarantee that the segmentation is complete and coherent. This means all the surface area, including any heavily occluded portions, should be labeled, and neighbouring surface areas should likely have the same label unless separated by a strong boundary feature.
- **Surface-based Conditional Random Field (CRF)** layer promotes consistent labeling of the entire surface and resolve missing surface information in the view representation.

# Evaluation
## Dataset
- ShapeNetCore: 17,773 segmented models, 16 categories.
- Labeled-PSB (L-PSB): 380 segmented models, 19 categories.
- COSEG: 190 segmented models, 8 categories.

## Metrics
- Input is a raw polygon mesh.
- Shape rendered as shaded, greyscale 512x512 images and depth images.
- 50% training/testing split.

## Results
- ShapeNetCore: there was an improvement of 5.4% on the state-of-the-art to an accuracy of **87.5%**.
- L-PSB & COSEG: **92.6%** accuracy.

# Resource
## Paper
https://arxiv.org/pdf/1612.02808.pdf

## Project page
https://people.cs.umass.edu/~kalo/papers/shapepfcn/

## Source code
https://github.com/kalov/ShapePFCN

## Build upon
- Currently our method uses a simple pairwise term based on surface distances and angles between surface normals. As a result, the segmentations can become noisy and not aligned with strong underlying mesh boundaries. Extracting robust boundaries through a learned module would be beneficial to our method.
- Our method currently deals with single-level, non-hierarchical segmentations. Further segmenting objects into fine-grained parts (e.g. segmenting motorbikes into sub-frame components) in a hierarchical manner would be useful in several vision and graphics applications.
- Another possibility for future work is to investigate different types of input to our network. The input images we used represent surface depth and normals relative to view direction. 
- Another possibility is to consider the HHA encoding or even raw position data. However, these encodings assume a consistent gravity direction or alignment for input 3D shapes. Although in a few repositories (e.g. Trimble Warehouse) the majority of 3D models have consistent upright orientation, this does not hold for all 3D models, and especially for other online repositories whose shapes are oriented along different, random axes.

## Paper connections
- Multi-view
- FCN
- CRF

## Software & Hardware
- C++
- Caffe
