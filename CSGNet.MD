# Basic info
- Title: CSGNet: Neural Shape Parser for Constructive Solid Geometry
- Author: Gopal Sharma, Rishabh Goyal, Difan Liu, Evangelos Kalogerakis, Subhransu Maji
- Affiliation: University of Massachusetts, Amherst
- Publication status: CVPR-2018 Conference Paper
- Short name: CSGNet
- Year: 2018

# Score
- Idea: 5
- Usability: 4
- Presentation: 4
- Overall: 4

# Contributions
## Problem addressed / Motivation
- CAD designers do not represent shape using enumerations of individual elements (e.g. pixels, voxels or points), which are currently used in generative model methods.
- Higher-level primitives are used instead such as: parametric curves (e.g. Bezier curves) or basic shapes (e.g. circles or polygons).
- The desired shape is produced by performing operations on the primitives (e.g. Boolean, deformation, extrusions).
- This allows for easy editability, compact design and captures human shape perception (e.g. view invariance, compositionality and symmetry).

## Idea / Observation / Contribution
- Develop a neural architecture for **shape parsing** into constituent modelling primitives and operations within the structure of **Constructive Solid Geometry (CSG)**.
- Efficient and effective architecture for creating CSG programs for 2D and 3D shapes.
- Shown that shape parsing can be performed on a new dataset by way of reinforcement learning without a target program.
- Shape parser outperforms other state-of-the-art detection approaches that only utilise bottom-up cues (this may be due to the aprser reasoning about the presence and order during parsing unlike detection). 

## Formulation / Solver / Implementation
- Utilize **autoencoder** (encoder = CNN & decoder = RNN) for neural shape parser.
- Decoder produces a probability distribution over programs represented by a sequence of instructions. 
- Gated Recurrent Units (GRU) used as RNN due to strong performance with sequential prediction tasks such as generation natural language and speech.
- The space of programs are described according to a **context-free grammar (CFG)**.
- If target programs are available, the architecture is trained with a supervised learning technique.
- Without target programs, a recontruction error is minimised between the shape obtained from the predicted program and the target shape (reinforcement learning).
- **Policy gradient** techniques used to minimise this error, as gradient descent is not possible due the output space is discrete and execution engines are usually not differentiable.
- Want to learn the network parameters that maximise the expected reward (the similarity between the generated and target shape measured using the *Chamfer distance CD*).
- **Beam search** used to predict the most likely instruction at each time step.
- **Visually-guided refinement** using the position and size of the primitives is used to maximise the reward, while keeping the primitive type the same.

## Useful info / tips
- The output does not have a constant dimensionality, due to the number of primitives and operations changes for different shapes.
- Order of operations matters.
- Method tries to generate program with fewest instructions.
- Not all programs are valid therefore the network has to learn to generate grammatical programs.

# Evaluation
## Dataset
- For supervised learning, the dataset consists of shape and program pairs.
- For unsupervised learning, the dataset consists of the shape only.


## Metrics
- designed different evaluation protocols by setting the gallery size to 50, 100, 500, 1, 000, 2, 000, and 4, 000
- meanAveraged Precision (mAP): A candidate window is considered as positive if its overlap with the ground truth is larger than 0.5
- top-k matching rate on bounding boxes: A matching is counted if a bounding box among the top-k predicted boxes overlaps with the ground truth larger than the threshold

## Results
- Baseline detector: ACF + Deep detector
- Baseline re-id methods: BoW with cosine distance, DenseSift+ColorHist with Euclidean and KISSME distance metric, IDNet

# Resource
## Project page
http://www.ee.cuhk.edu.hk/~xgwang/PS/dataset.html

## Source code
- 2D Code: https://github.com/Hippogriff/CSGNet
- 3D Code: https://github.com/Hippogriff/3DCSGNet

## Dataset
Need to send request
https://drive.google.com/open?id=0B-GOvBat1maOVUE3WmNNUVRGamc

## Other paper reading notes

## Others

# Questions
- How to perform re-id algorithm in current framework?

# Build upon
- Generalise approach for longer programs (more advanced reward functions to balance perceptual similarity to the input image and program length).
- Explore combining bottom-up proposals and top-down approaches for shape parsing, in addition to exploring top-down program generation strategies.
- Look into producing extrusion feature tree instead of CSG program.
- Possibility of reduced order modelling.

# Paper connections
- Faster RCNN

