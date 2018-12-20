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
- Primitive types: 2D (*square, circle* or *triangle*), 3D (*cube, sphere* or *cylinder*).
- Datasets consisted of:
  1. Automatically generated dataset of 2D and 3D shapes using CSG programs (Supervised).
  2. 2D CAD shapes from web where ground-truth programs are not available (Unsupervised).
  3. Logo images from web where ground-truth programs are not available (Unsupervised).

## Metrics
- For 2D CSG, there were 400 unique instructions corresponding to 396 different primitve types, discrete locations and sizes, the 3 boolean operations and the stop symbols.
- For 3D CSG, there were 6635 unique instructions with 6631 different types of primitves with different sizes and locations, plus 3 boolean modelling operations and a top symbol.
- 64x64x64 voxelised input.

## Results
- Different beam sizes (k = 1, 5 & 10) compared using Nearest Neighbour with k = 10 giving the lowest CD of 1.39.
- Shape parser is evaluated as a primitive detector (output primitves of program evualated instead of operations), allowing for direct comparision to bottom-up object detection techniques (Faster R-CNN based on VGG-M network and Hough tranform).
- CSGNet (k = 40) outperformed R-CNN for circle, square and triangle detection whith a higher speed on the same GPU (NVIDA 1070).

# Resource
## Project page

## Source code
- 2D Code: https://github.com/Hippogriff/CSGNet
- 3D Code: https://github.com/Hippogriff/3DCSGNet

## Dataset
 
## Other paper reading notes

## Others
- PyTorch.

# Questions

# Build upon
- Generalise approach for longer programs (more advanced reward functions to balance perceptual similarity to the input image and program length).
- Explore combining bottom-up proposals and top-down approaches for shape parsing, in addition to exploring top-down program generation strategies.
- Look into producing extrusion feature tree instead of CSG program.
- Possibility of reduced order modelling.

# Paper connections
- Faster R-CNN

