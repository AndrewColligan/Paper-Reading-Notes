# Basic info
- Title: DeepPano: Deep Panoramic Representation for 3-D Shape Recognition
- Author: Baoguang Shi, Song Bai, Zhichao Zhou & Xiang Bai
- Affiliation: School of Electronic Information and Communications, Huazhong University of Science and Technology, Wuhan, China
- Publication status: IEEE Signal Processing Letters, Vol. 22, No. 12, December 2015
- Short name: DeepPano
- Year: 2015

# Score
- Idea: 4
- Usability: 2
- Presentation: 5
- Overall: 3

# Contributions
## Problem addressed / Motivation
- One of the most important challenges in 3D shape analysis is to obtain a good representation for shapes. 
- The performance of many tasks, including shape classification and shape retrieval, heavily depend on the quality of the representation.

## Idea / Observation / Contribution
- Propose a shape descriptor for 3D shape classification and retrieval, which is directly learned from the panoramic views of 3D models.
- The panoramic view is a cylinder projection of a 3D model around its principal axis.
- Panoramic views are in the form of 2D images, which can be considered as a holistic representation of 3D models.
- This enables the use of 2D CNN to learn a deep representation from such views.

## Formulation / Solver / Implementation
- Related to previous PANORAMA by Panagiotis et al, but panoramic view shifts when the 3D shape rotates along its principle axis.
- They pool the response of each row so that the resulting representation is not affected by this kind of shift.
- A variant of CNN is created to learn and extract the representation, to handle several issues.
- To avoid **boundary artifacts**, the panoramic view is padded on one side.
- To make the learned deep features **invariant** to the **rotation** around the principle axis, a special layer named *Row-Wise Max-Pooling (RWMP)* layer is presented and inserted between the convolution layers and the fully-connected layers.
- This layer take the maximum value of each row in the convolutional feature maps.
- Softmax layer on the top of the network outputs class probabilites, and the class with the highest probability is taken as the prediction.

## Info/Tips
- AUC - Mean area under precision-recall curve
- MAP - Mean average precision

# Evaluation
## Dataset
- ModelNet10
- ModelNet40

## Metrics
- Assumes that 3D models are upright oriented.
- 11 rotations are performed (30, 60, ..., 330).

## Results

#### Classification
- ModelNet10: 88.66%
- ModelNet40: 82.54%
- Reason why it is better than ShapeNet is because the rotation invariance is hard-coded into the network architecture, making the representation rotation invariant.

#### Shape Retrieval

| Method          | ModelNet10 |    | ModelNet40 |    |
| --------------- | ------ | ------ | ------ | ------ |
|                 | AUC    | MAP    | AUC    | MAP    |
| DeepPano (RWMP) | 70.76% | 69.88% | 56.68% | 56.14% |
| DeepPano (fc1)  | 84.47% | 83.52% | 74.57% | 73.92% |
| DeepPano (fc2)  | **85.45%** | **84.18%** | **77.63%** | **76.81%** |

# Resource
## Paper
https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=7273863

## Source code
https://github.com/bgshih/deeppano

## Build Upon
- Limitation of apporach is similar to many previous view-based approaches, requiring the principle axes of 3D models, which, may fail to recognise the 3D models with serious non-rigid deformation.
- Some sequence prediction techniques might be used for exploring more contextual information, in order to further improve the performance of shape recognition, as a panoramic view can be considered as a map of feature sequence.
- Estabilish robust alignments/correspondence between different panoramic views.

## Paper connections
- Multi-view

## Software & Hardware
- Torch7
- Matlab
- Intel Core-i5
- Nvidia GTX780 GPU
- 8 GB RAM
- Training less than 4 hours
