# Basic info
- Title: Generative and Discriminative Voxel Modeling with Convolutional Neural Networks
- Author: Andrew Brock, Theodore Lim, J.M. Ritchie & Nick Weston
- Affiliation: School of Engineering and Physical Sciences, Heriot-Watt University, Edinburgh, UK & Renishaw plc, Research Ave, North Edinburgh, UK
- Publication status: 
- Short name: VRN
- Year: 2016

# Score
- Idea: 3
- Usability: 4
- Presentation: 4
- Overall: 4

# Contributions
## Problem addressed / Motivation
- 3D data offer computer vision systems a rich view of the world, but also pose a unique set of challenges, particulary in applications where understanding the surrounding environment is critical.
- In particular, data such as a point cloud extracted from an RGB-D image or a polygonal mesh are not guaranteed to be arranged in a regular grid, making them unsuitable for use with high-performance machine learning algorithms such as CNN.

## Idea / Observation / Contribution
- Use a Variational Autoencoder (VAE), a probabilistic framework that learns both an inference network to map from an input space to a set of descriptive latent variables, and a generative network that maps from the latent space to the input space.
- By training a network to infer the latent variables which describe the underlying factors of variation between objects, the ability to smoothly transition between objects by interpolating between each object's latent description and reconstructing using the decoder networis gained.
- Voxels used to give a regular input.
- Create user interface.

## Formulation / Solver / Implementation
- Autoencoder made of two 3D CNN with up to 45 layers.
- Adopt a simple **Inception-style architecture** with the intuition of maximising the number of possible "pathways" for information to propagate through the network, while still maintaining simplicity and efficiency. 
- Loss function consisted of the KL divergence prior on latents, L2 weight regularisation and reconstruction error which used a altered form of Binary Cross-Entropy (BCE).
- The data is augmented by adding random translations and horizontal flips to each training example.
- Same as VoxNet, two versions of the training set are used: 12 rotations of each instance and 24 rotations of each instance.
- Experimented with different rotations as separate channels for a single instance, but found that training a model to look at a single orientation and averaging predictions across rotated versions of an instance yielded better performance.
- Experimented with a variety of values for the range of the binary voxel grid, including an adaptive method wherein the numerical value of positive entries is equal to the 100 times the percentage of the grid occupied by the object, but did not find these methods to significantly alter performance.

# Evaluation
## Dataset
- ModelNet10
- ModelNet40

## Metrics
- 32x32x32 voxel resolution.

## Results
#### Reconstruction accuracy on ModelNet10

|            | Predicted +ve | Predicted -ve |
| ---------- | ------------- | ------------- |
| Actual +ve | 99.39%        | 0.61%         |
| Actual -ve | 7.64%         | 92.36%        |

- Network struggled for long, thin members such as chairs. This is suspected because these features are too small to activate in the receptive field of the appropiate latents, and are lost in favor of denser features which weight more heavily in the loss function, and suggest imposing an additional *local* reconstruction function that measures reconstruction accuracy in subsets of the voxel grid.

#### Classification accuracy

| Model        | ModelNet40 | ModelNet10 |
| ------------ | ---------- | ---------- |
| VRN (1-view) | 88.98%     | -          |
| VRN          | 91.33%     | 93.61%     |
| VRN Ensemble | **95.54%** | **97.14%** |

- Suspected that their deeper model does not perform as well when trained on the smaller subset of ModelNet10 due to a lack of data. Other papers such as ORION incorporates class-specific priors to determine precisely which rotations to trian on, where as their network favours generality.

# Resource
## Paper
https://arxiv.org/abs/1608.04236

## Source code
https://github.com/ajbrock/Generative-and-Discriminative-Voxel-Modeling

## Build upon
- Refine the voxel grid beyond 32x32x32 to increase spatial resolution and improve the available detail.
- Change the voxel grid to be real-valued based on the percentage of space occupied by the instance at each grid element. This could also be used with the VAE to allow it to represent more complex shapes by fitting a corner-connected polyhedron with volume equal to the predicted occupancy percentage.
- Experiment with more data augmentation, such as rotating about random axes (or just adding more rotations about the central axis), random crops, or random rescaling.
- Try out different Voxception architectures, downsampling methods, and activation functions. Our experiments focused primarily on high-level network architecture, and there are likely more effective ways to compose a Voxception-ResNet block.

## Paper connections
- Voxel
- 3D CNN
- Autoencoder

## Software & Hardware
- GT730m graphic card.
- Titan X (6 hours for 1 epoch, 6 days of training to converge).
- Theano with Lasagne.
- VTK for user interface.
