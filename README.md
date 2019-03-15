# Paper Categories
Academic papers organised into their appropiate categories.

**Machine Learning** are organised by their shape format:
- [Geodesic](#geodesic)
- [Graph](#graph)
- [Hybrid](#hybrid)
- [Mutli-View](#multi-view)
- [Octree](#octree)
- [Point Cloud](#point-cloud)
- [Primitives](#primitives)
- [Voxels](#voxels)


# Machine Learning
## Hybrid
### 2016
<details>
 <summary><b>FusionNet: 3D Object Classification Using Multiple Data Representation</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/FusionNet.md">[Paper Note]</a></summary>
<hr>
 <p align="justify">
High-quality 3D object recognition is an important component of many vision and robotics systems. We tackle the object recognition problem using two data representations: Volumetric representation, where the 3D object is discretized spatially as binary voxels - 1 if the voxel is occupied and 0 otherwise. Pixel representation where the 3D object is represented as a set of projected 2D pixel images. At the time of submission, we obtained leading results on the Princeton ModelNet challenge. Some of the best deep learning architectures for classifying 3D CAD models use Convolutional Neural Networks (CNNs) on pixel representation, as seen on the ModelNet leaderboard. Diverging from this trend, we combine both the above representations and exploit them to learn new features. This approach yields a significantly better classifier than using either of the representations in isolation. To do this, we introduce new Volumetric CNN (V-CNN) architectures.
  </p>
<hr>
</details>


## Multi-View
### 2015
<details>
 <summary><b>Multi-view Convolutional Neural Networks for 3D Shape Recognition</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/MV-CNN.md">[Paper Note]</a></summary>
<hr>
 <p align="justify">
A longstanding question in computer vision concerns the representation of 3D shapes for recognition: should 3D shapes be represented with descriptors operating on their native 3D formats, such as voxel grid or polygon mesh, or can they be effectively represented with view-based descriptors? We address this question in the context of learning to recognize 3D shapes from a collection of their rendered views on 2D images. We first present a standard CNN architecture trained to recognize the shapes’ rendered views independently of each other, and show that a 3D shape can be recognized even from a single view at an accuracy far higher than using state-of-the-art 3D shape descriptors. Recognition rates further increase when multiple views of the shapes are provided. In addition, we present a novel CNN architecture that combines information from multiple views of a 3D shape into a single and compact shape descriptor offering even better recognition performance. The same architecture can be applied to accurately recognize human hand-drawn sketches of shapes. We conclude that a collection of 2D views can be highly informative for 3D shape recognition and is amenable to emerging CNN architectures and their derivatives.
  </p>
<hr>
</details>

## Octree
### 2017
<details>
 <summary><b>O-CNN: Octree-based Convolutional Neural Networks for 3D Shape Analysis</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/O-CNN.md">[Paper Note]</a></summary>
<hr>
 <p align="justify">
We present O-CNN, an Octree-based Convolutional Neural Network (CNN) for 3D shape analysis. Built upon the octree representation of 3D shapes, our method takes the average normal vectors of a 3D model sampled in the finest leaf octants as input and performs 3D CNN operations on the octants occupied by the 3D shape surface. We design a novel octree data structure to efficiently store the octant information and CNN features into the graphics memory and execute the entire O-CNN training and evaluation on the GPU. O-CNN supports various CNN structures and works for 3D shapes in different representations. By restraining the computations on the octants occupied by 3D surfaces, the memory and computational costs of the O-CNN grow quadratically as the depth of the octree increases, which makes the 3D CNN feasible for high-resolution 3D models. We compare the performance of the O-CNN with other existing 3D CNN solutions and demonstrate the efficiency and efficacy of O-CNN in three shape analysis tasks, including object classification, shape retrieval, and shape segmentation.
  </p>
<hr>
</details>


## Point Cloud
### 2017
<details>
 <summary><b>PointNet: Deep Learning on Point Sets for 3D Classification and Segmentation</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/PointNet.md">[Paper Note]</a></summary>
<hr>
 <p align="justify">
Point cloud is an important type of geometric data structure. Due to its irregular format, most researchers transform such data to regular 3D voxel grids or collections of images. This, however, renders data unnecessarily voluminous and causes issues. In this paper, we design a novel type of neural network that directly consumes point clouds, which well respects the permutation invariance of points in the input. Our network, named PointNet, provides a unified architecture for applications ranging from object classification, part segmentation, to scene semantic parsing. Though simple, PointNet is highly efficient and effective.Empirically, it shows strong performance on par or even better than state of the art. Theoretically, we provide analysis towards understanding of what the network has learnt and why the network is robust with respect to input perturbation and corruption.
</p>
<hr>
</details>

## Primitives
### 2018
<details>
 <summary><b>Physical Primitive Decomposition</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/PPD.md">[Paper Note]</a></summary>
 <hr>
 <p align="justify">
Objects are made of parts, each with distinct geometry, physics, functionality, and affordances. Developing such a distributed, physical, interpretable representation of objects will facilitate intelligent agents to better explore and interact with the world. In this paper, we study physical primitive decomposition|understanding an object through its components, each with physical and geometric attributes. As annotated data for object parts and physics are rare, we propose a novel formulation that learns physical primitives by explaining both an object's appearance and its behaviors in physical events. Our model performs well on block towers and tools in both synthetic and real scenarios; we also demonstrate that visual and physical observations often provide comple- mentary signals. We further present ablation and behavioral studies to better understand our model and contrast it with human performance.
 </p>
 <hr>
</details>

<details>
 <summary><b>CSGNet: Neural Shape Parser for Constructive Solid Geometry</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/CSGNet.MD">[Paper Note]</a></summary>
 <hr>
 <p align="justify">
We present a neural architecture that takes as input a 2D or 3D shape and outputs a program that generates the shape. The instructions in our program are based on constructive solid geometry principles, i.e., a set of boolean operations on shape primitives defined recursively. Bottomup techniques for this shape parsing task rely on primitive detection and are inherently slow since the search space over possible primitive combinations is large. In contrast, our model uses a recurrent neural network that parses the input shape in a top-down manner, which is significantly faster and yields a compact and easy-to-interpret sequence of modeling instructions. Our model is also more effective as a shape detector compared to existing state-of-the-art detection techniques. We finally demonstrate that our network can be trained on novel datasets without ground-truth program annotations through policy gradient techniques.
 </p>
 <hr>
</details>


### 2017
<details>
 <summary><b>3D-PRNN: Generating Shape Primitives with Recurrent Neural Networks</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/3D-PRNN.md">[Paper Note]</a></summary>
 <hr>
 <p align="justify">
The success of various applications including robotics, digital content creation, and visualization demand a structured and abstract representation of the 3D world from limited sensor data. Inspired by the nature of human perception of 3D shapes as a collection of simple parts, we explore such an abstract shape representation based on primitives. Given a single depth image of an object, we present 3DPRNN, a generative recurrent neural network that synthesizes multiple plausible shapes composed of a set of primitives. Our generative model encodes symmetry characteristics of common man-made objects, preserves long-range structural coherence, and describes objects of varying complexity with a compact representation. We also propose a method based on Gaussian Fields to generate a large scale dataset of primitive-based shape representations to train our network. We evaluate our approach on a wide range of examples and show that it outperforms nearest-neighbor based shape retrieval methods and is on-par with voxelbased generative models while using a significantly reduced parameter space.
 </p>
 <hr>
</details>

## Voxels
### 2018
<details>
 <summary><b>Learning localized features in 3D CAD models for manufacturability analysis of drilled holes</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/DLDFM.md">[Paper Note]</a></summary>
 <hr>
 <p align="justify">
We present a novel feature identification framework to recognize difficult-to-manufacture drilled holes in a complex CAD geometry using deep learning. Deep learning algorithms have been successfully used in object recognition, video analytics, image segmentation, etc. Specifically, 3D Convolutional Neural Networks (3D-CNNs) have been used for object recognition from 3D voxel data based on the external shape of an object. On the other hand, manufacturability of a component depends on local features more than the external shape. Learning these local features from a boundary representation (B-Rep) CAD model is challenging due to lack of volumetric information. In this paper, we learn local features from a voxelized representation of a CAD model and classify its manufacturability. Further, to enable effective learning of localized features, we augment the voxel data with surface normals of the object boundary. We train a 3D-CNN with this augmented data to identify local features and classify the manufacturability. However, this classification does not provide information about the source of non-manufacturability in a complex component. Therefore, we have developed a 3D-CNN based gradient-weighted class activation mapping (3D-GradCAM) method that can provide visual explanations of the local geometric features of interest within an object. Using 3D-GradCAM, our framework can identify difficult-to-manufacture features, which allows a designer to modify the component based on its manufacturability and thus improve the design process. We extend this framework to identify difficult-to-manufacture features in a realistic CAD model with multiple drilled holes, which can ultimately enable development of a real-time manufacturability decision support system.
  </p>
 <hr>
</details>

<details>
 <summary><b>FeatureNet: Machining Feature Recognition Based on 3D Convolution Neural Network</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/FeatureNet.md">[Paper Note]</a></summary>
 <hr>
 <p align="justify">
Automated machining feature recognition, a sub-discipline of solid modeling, has been an active research area for last three decades and is a critical component in digital manufacturing thread for detecting manufacturing information from computer aided design (CAD) models. In this paper, a novel framework using Deep 3D Convolutional Neural Networks (3D-CNNs) termed FeatureNet to learn machining features from CAD models of mechanical parts is presented. FeatureNet learns the distribution of complex manufacturing feature shapes across a large 3D model dataset and discovers distinguishing features that help in recognition process automatically. To train FeatureNet, a large-scale mechanical part datasets of 3D CAD models with labeled machining features is automatically constructed. The proposed framework can recognize manufacturing features from the low-level geometric data such as voxels with a very high accuracy. The developed framework can also recognize planar intersecting features in the 3D CAD models. Extensive numerical experiments show that FeatureNet enables significant improvements over the state-of-the-arts manufacturing feature detection techniques. The developed data-driven framework can easily be extended to identify a large variety of machining features leading to a sound foundation for real-time computer aided process planning (CAPP) systems.
 </p>
 <hr>
</details>

### 2015
<details>
 <summary><b>3D ShapeNets: A Deep Representation for Volumetric Shapes</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/ShapeNet.md">[Paper Note]</a></summary>
 <hr>
 <p align="justify">
 3D shape is a crucial but heavily underutilized cue in today’s computer vision systems, mostly due to the lack of a good generic shape representation. With the recent availability of inexpensive 2.5D depth sensors (e.g. Microsoft Kinect), it is becoming increasingly important to have a powerful 3D shape representation in the loop. Apart from category recognition, recovering full 3D shapes from viewbased 2.5D depth maps is also a critical part of visual understanding. To this end, we propose to represent a geometric 3D shape as a probability distribution of binary variables on a 3D voxel grid, using a Convolutional Deep Belief Network. Our model, 3D ShapeNets, learns the distribution of complex 3D shapes across different object categories and arbitrary poses from raw CAD data, and discovers hierarchical compositional part representation automatically. It naturally supports joint object recognition and shape completion from 2.5D depth maps, and it enables active object recognition through view planning. To train our 3D deep learning model, we construct ModelNet – a largescale 3D CAD model dataset. Extensive experiments show that our 3D deep representation enables significant performance improvement over thestateofthearts in a variety of tasks.
 <hr>
 </p>
</details>
      
