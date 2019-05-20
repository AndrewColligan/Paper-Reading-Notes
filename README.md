# Paper Categories
Academic papers organised into their appropiate categories.

**Machine Learning for 3D** are organised by their shape format:
- [Graph](#graph)
- [Hybrid](#hybrid)
- [Manifolds & Meshes](#manifolds-and-meshes)
- [Multi-View](#multi-view)
- [Octree](#octree)
- [Other](#other)
- [Point Cloud](#point-cloud)
- [Primitives](#primitives)
- [Voxels](#voxels)

**Other Machine Learning Papers**
- [Networks](#networks)


# Machine Learning for 3D
## Hybrid
### 2018
<details>
 <summary><b>PointGrid: A Deep Network for 3D Shape Understanding</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Hybrid/PointGrid.md">[Paper Note]</a></summary>
<hr>
 <p align="justify">
Volumetric grid is widely used for 3D deep learning due to its regularity. However the use of relatively lower order local approximation functions such as piece-wise constant function (occupancy grid) or piece-wise linear function (distance field) to approximate 3D shape means that it needs a very high-resolution grid to represent finer geometry details, which could be memory and computationally inefficient. In this work, we propose the PointGrid, a 3D convolutional network that incorporates a constant number of points within each grid cell thus allowing the network to learn higher order local approximation functions that could better represent the local geometry shape details. With experiments on popular shape recognition benchmarks, PointGrid demonstrates state-of-the-art performance over existing deep learning methods on both classification and segmentation.
</p>
<hr>
</details>

<details>
 <summary><b>NormalNet: A voxel-based CNN for 3D object classification and retrieval</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Hybrid/NormalNet.md">[Paper Note]</a></summary>
<hr>
 <p align="justify">
A common approach to tackle 3D object recognition tasks is to project 3D data to multiple 2D images. Projection only captures the outline of the object, and discards the internal information that may be crucial for the recognition. In this paper, we stay in 3D and concentrate on tapping the potential of 3D representations. We present NormalNet, a voxel-based convolutional neural network (CNN) designed for 3D object recognition. The network uses normal vectors of the object surfaces as input, which demonstrate stronger discrimination capability than binary voxels. We propose a reflection–convolution–concatenation (RCC) module to realize the conv layers, which extracts distinguishable features for 3D vision tasks while reducing the number of parameters significantly. We further improve the performance of NormalNet by combining two networks, which take normal vectors and voxels as input respectively. We carry out a series of experiments that validate the design of the network and achieve competitive performance in 3D object classification and retrieval tasks.
</p>
<hr>
</details>

### 2016
<details>
 <summary><b>FusionNet: 3D Object Classification Using Multiple Data Representation</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Hybrid/FusionNet.md">[Paper Note]</a></summary>
<hr>
 <p align="justify">
High-quality 3D object recognition is an important component of many vision and robotics systems. We tackle the object recognition problem using two data representations: Volumetric representation, where the 3D object is discretized spatially as binary voxels - 1 if the voxel is occupied and 0 otherwise. Pixel representation where the 3D object is represented as a set of projected 2D pixel images. At the time of submission, we obtained leading results on the Princeton ModelNet challenge. Some of the best deep learning architectures for classifying 3D CAD models use Convolutional Neural Networks (CNNs) on pixel representation, as seen on the ModelNet leaderboard. Diverging from this trend, we combine both the above representations and exploit them to learn new features. This approach yields a significantly better classifier than using either of the representations in isolation. To do this, we introduce new Volumetric CNN (V-CNN) architectures.
  </p>
<hr>
</details>

<details>
 <summary><b>Volumetric and Multi-View CNNs for Object Classification on 3D Data</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Hybrid/VMVC.md">[Paper Note]</a></summary>
<hr>
 <p align="justify">
<b>Not a hybrid but two separate methods.</b>
3D shape models are becoming widely available and easier to capture, making available 3D information crucial for progress in object classification. Current state-of-the art methods rely on CNNs to address this problem. Recently, we witness two types of CNNs being developed: CNNs based upon volumetric representations versus CNNs based upon multi-view representations. Empirical results from these two types of CNNs exhibit a large gap, indicating that existing volumetric CNN architectures and approaches are unable to fully exploit the power of 3D representations. In this paper, we aim to improve both volumetric CNNs and multi-view CNNs according to extensive analysis of existing approaches. To this end, we introduce two distinct network architectures of volumetric CNNs. In addition, we examine multi-view CNNs, where we introduce multiresolution filtering in 3D. Overall, we are able to outperform current state-of-the-art methods for both volumetric CNNs and multi-view CNNs. We provide extensive experiments designed to evaluate underlying design choices, thus providing a better understanding of the space of methods available for object classification on 3D data.  
  </p>
<hr>
</details>

## Manifolds-and-Meshes
### 2019
<details>
 <summary><b>MeshNet: Mesh Neural Network for 3D Shape Recognition</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Manifolds/MeshNet.md">[Paper Note]</a></summary>
<hr>
 <p align="justify">
Mesh is an important and powerful type of data for 3D shapes and widely studied in the field of computer vision and computer graphics. Regarding the task of 3D shape representation, there have been extensive research efforts concentrating on how to represent 3D shapes well using volumetric grid, multi-view and point cloud. However, there is little effort on using mesh data in recent years, due to the complexity and irregularity of mesh data. In this paper, we propose a mesh neural network, named MeshNet, to learn 3D shape representation from mesh data. In this method, face-unit and feature splitting are introduced, and a general architecture with available and effective blocks are proposed. In this way, MeshNet is able to solve the complexity and irregularity problem of mesh and conduct 3D shape representation well.We have applied the proposed MeshNet method in the applications of 3D shape classification and retrieval. Experimental results and comparisons with the state-of-the-art methods demonstrate that the proposed MeshNet can achieve satisfying 3D shape classification and retrieval performance, which indicates the  effectiveness of the proposed method on 3D shape representation.
  </p>
<hr>
</details>

### 2015
<details>
 <summary><b>Geodesic Convolutional Neural Networks on Riemannian Manifolds</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Manifolds/GCNN.md">[Paper Note]</a></summary>
<hr>
 <p align="justify">
Feature descriptors play a crucial role in a wide range of geometry analysis and processing applications, including shape correspondence, retrieval, and segmentation. In this paper, we introduce Geodesic Convolutional Neural Networks (GCNN), a generalization of the convolutional networks (CNN) paradigm to non-Euclidean manifolds. Our construction is based on a local geodesic system of polar coordinates to extract "patches", which are then passed through a cascade of filters and linear and non-linear operators. The coefficients of the filters and linear combination weights are optimization variables that are learned to minimize a task-specific cost function. We use GCNN to learn invariant shape features, allowing to achieve state-of-the-art performance in problems such as shape description, retrieval, and correspondence.
  </p>
<hr>
</details>


## Multi-View
### 2017
<details>
 <summary><b>3D Shape Segmentation with Projective Convolutional Networks</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Multi-View/ShapePFCN.md">[Paper Note]</a></summary>
<hr>
 <p align="justify">
This paper introduces a deep architecture for segmenting 3D objects into their labeled semantic parts. Our architecture combines image-based Fully Convolutional Networks (FCNs) and surface-based Conditional Random Fields (CRFs) to yield coherent segmentations of 3D shapes. The image-based FCNs are used for efficient view-based reasoning about 3D object parts. Through a special projection layer, FCN outputs are effectively aggregated across multiple views and scales, then are projected onto the 3D object surfaces. Finally, a surface-based CRF combines the projected outputs with geometric consistency cues to yield coherent segmentations. The whole architecture (multi-view FCNs and CRF) is trained end-to-end. Our approach significantly outperforms the existing stateof-the-art methods in the currently largest segmentation benchmark (ShapeNet). Finally, we demonstrate promising segmentation results on noisy 3D shapes acquired from consumer-grade depth cameras.
  </p>
<hr>
</details>

### 2015
<details>
 <summary><b>DeepPano: Deep Panoramic Representation for 3-D Shape Recognition</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Multi-View/DeepPano.md">[Paper Note]</a></summary>
<hr>
 <p align="justify">
This letter introduces a robust representation of 3-D shapes, named DeepPano, learned with deep convolutional neural networks (CNN). Firstly, each 3-D shape is converted into a panoramic view, namely a cylinder projection around its principle axis. Then, a variant of CNN is specifically designed for learning the deep representations directly from such views. Different from typical CNN, a row-wise max-pooling layer is inserted between the convolution and fully-connected layers, making the learned representations invariant to the rotation around a principle axis. Our approach achieves state-of-the-art retrieval/classification results on two large-scale 3-D model datasets (ModelNet-10 and ModelNet-40), outperforming typical methods by a large margin. 
  </p>
<hr>
</details>

<details>
 <summary><b>Multi-view Convolutional Neural Networks for 3D Shape Recognition</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Multi-View/MV-CNN.md">[Paper Note]</a></summary>
<hr>
 <p align="justify">
A longstanding question in computer vision concerns the representation of 3D shapes for recognition: should 3D shapes be represented with descriptors operating on their native 3D formats, such as voxel grid or polygon mesh, or can they be effectively represented with view-based descriptors? We address this question in the context of learning to recognize 3D shapes from a collection of their rendered views on 2D images. We first present a standard CNN architecture trained to recognize the shapes’ rendered views independently of each other, and show that a 3D shape can be recognized even from a single view at an accuracy far higher than using state-of-the-art 3D shape descriptors. Recognition rates further increase when multiple views of the shapes are provided. In addition, we present a novel CNN architecture that combines information from multiple views of a 3D shape into a single and compact shape descriptor offering even better recognition performance. The same architecture can be applied to accurately recognize human hand-drawn sketches of shapes. We conclude that a collection of 2D views can be highly informative for 3D shape recognition and is amenable to emerging CNN architectures and their derivatives.
  </p>
<hr>
</details>

## Octree
### 2017
<details>
 <summary><b>OctNet: Learning Deep 3D Representations at High Resolutions</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Octree/OctNet.md">[Paper Note]</a></summary>
<hr>
 <p align="justify">
We present OctNet, a representation for deep learning with sparse 3D data. In contrast to existing models, our representation enables 3D convolutional networks which are both deep and high resolution. Towards this goal, we exploit the sparsity in the input data to hierarchically partition the space using a set of unbalanced octrees where each leaf node stores a pooled feature representation. This allows to focus memory allocation and computation to the relevant dense regions and enables deeper networks without compromising resolution. We demonstrate the utility of our OctNet representation by analyzing the impact of resolution on several 3D tasks including 3D object classification, orientation estimation and point cloud labeling.
  </p>
<hr>
</details>

<details>
 <summary><b>O-CNN: Octree-based Convolutional Neural Networks for 3D Shape Analysis</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Octree/O-CNN.md">[Paper Note]</a></summary>
<hr>
 <p align="justify">
We present O-CNN, an Octree-based Convolutional Neural Network (CNN) for 3D shape analysis. Built upon the octree representation of 3D shapes, our method takes the average normal vectors of a 3D model sampled in the finest leaf octants as input and performs 3D CNN operations on the octants occupied by the 3D shape surface. We design a novel octree data structure to efficiently store the octant information and CNN features into the graphics memory and execute the entire O-CNN training and evaluation on the GPU. O-CNN supports various CNN structures and works for 3D shapes in different representations. By restraining the computations on the octants occupied by 3D surfaces, the memory and computational costs of the O-CNN grow quadratically as the depth of the octree increases, which makes the 3D CNN feasible for high-resolution 3D models. We compare the performance of the O-CNN with other existing 3D CNN solutions and demonstrate the efficiency and efficacy of O-CNN in three shape analysis tasks, including object classification, shape retrieval, and shape segmentation.
  </p>
<hr>
</details>

## Other
### 2017
<details>
 <summary><b>Escape from Cells: Deep Kd-Networks for the Recognition of 3D Point Cloud Models</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Other/Kd-network.md">[Paper Note]</a></summary>
<hr>
 <p align="justify">
We present a new deep learning architecture (called Kdnetwork) that is designed for 3D model recognition tasks and works with unstructured point clouds. The new architecture performs multiplicative transformations and shares parameters of these transformations according to the subdivisions of the point clouds imposed onto them by kdtrees. Unlike the currently dominant convolutional architectures that usually require rasterization on uniform twodimensional or three-dimensional grids, Kd-networks do not rely on such grids in any way and therefore avoid poor scaling behavior. In a series of experiments with popular shape recognition benchmarks, Kd-networks demonstrate competitive performance in a number of shape recognition tasks such as shape classification, shape retrieval and shape part segmentation. 
  </p>
<hr>
</details>

## Point Cloud

### 2017
<details>
 <summary><b>PointCNN: Convolution On X-Transformed Points</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Point-Cloud/PointCNN.md">[Paper Note]</a></summary>
<hr>
 <p align="justify">
We present a simple and general framework for feature learning from point clouds. The key to the success of CNNs is the convolution operator that is capable of leveraging spatially-local correlation in data represented densely in grids (e.g. images). However, point clouds are irregular and unordered, thus directly convolving kernels against features associated with the points will result in desertion of shape information and variance to point ordering. To address these problems, we propose to learn an X-transformation from the input points to simultaneously promote two causes: the first is the weighting of the input features associated with the points, and the second is the permutation of the points into a latent and potentially canonical order. Element-wise product and sum operations of the typical convolution operator are subsequently applied on the X-transformed features. The proposed method is a generalization of typical CNNs to feature learning from point clouds, thus we call it PointCNN. Experiments show that PointCNN achieves on par or better performance than state-of-the-art methods on multiple challenging benchmark datasets and tasks.
</p>
<hr>
</details>

### 2017
<details>
 <summary><b>PointNet++: Deep Hierarchical Feature Learning on Point Sets in a Metric Space</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Point-Cloud/PointNet%2B%2B.md">[Paper Note]</a></summary>
<hr>
 <p align="justify">
Few prior works study deep learning on point sets. PointNet is a pioneer in this direction. However, by design PointNet does not capture local structures induced by the metric space points live in, limiting its ability to recognize fine-grained patterns and generalizability to complex scenes. In this work, we introduce a hierarchical neural network that applies PointNet recursively on a nested partitioning of the input point set. By exploiting metric space distances, our network is able to learn local features with increasing contextual scales. With further observation that point sets are usually sampled with varying densities, which results in greatly decreased performance for networks trained on uniform densities, we propose novel set learning layers to adaptively combine features from multiple scales. Experiments show that our network called PointNet++ is able to learn deep point set features efficiently and robustly. In particular, results significantly better than state-of-the-art have been obtained on challenging benchmarks of 3D point clouds.
</p>
<hr>
</details>

<details>
 <summary><b>PointNet: Deep Learning on Point Sets for 3D Classification and Segmentation</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Point-Cloud/PointNet.md">[Paper Note]</a></summary>
<hr>
 <p align="justify">
Point cloud is an important type of geometric data structure. Due to its irregular format, most researchers transform such data to regular 3D voxel grids or collections of images. This, however, renders data unnecessarily voluminous and causes issues. In this paper, we design a novel type of neural network that directly consumes point clouds, which well respects the permutation invariance of points in the input. Our network, named PointNet, provides a unified architecture for applications ranging from object classification, part segmentation, to scene semantic parsing. Though simple, PointNet is highly efficient and effective.Empirically, it shows strong performance on par or even better than state of the art. Theoretically, we provide analysis towards understanding of what the network has learnt and why the network is robust with respect to input perturbation and corruption.
</p>
<hr>
</details>

## Primitives
### 2018
<details>
 <summary><b>CSGNet: Neural Shape Parser for Constructive Solid Geometry</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Primitives/CSGNet.md">[Paper Note]</a></summary>
 <hr>
 <p align="justify">
We present a neural architecture that takes as input a 2D or 3D shape and outputs a program that generates the shape. The instructions in our program are based on constructive solid geometry principles, i.e., a set of boolean operations on shape primitives defined recursively. Bottomup techniques for this shape parsing task rely on primitive detection and are inherently slow since the search space over possible primitive combinations is large. In contrast, our model uses a recurrent neural network that parses the input shape in a top-down manner, which is significantly faster and yields a compact and easy-to-interpret sequence of modeling instructions. Our model is also more effective as a shape detector compared to existing state-of-the-art detection techniques. We finally demonstrate that our network can be trained on novel datasets without ground-truth program annotations through policy gradient techniques.
 </p>
 <hr>
</details>

<details>
 <summary><b>Physical Primitive Decomposition</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Primitives/PPD.md">[Paper Note]</a></summary>
 <hr>
 <p align="justify">
Objects are made of parts, each with distinct geometry, physics, functionality, and affordances. Developing such a distributed, physical, interpretable representation of objects will facilitate intelligent agents to better explore and interact with the world. In this paper, we study physical primitive decomposition understanding an object through its components, each with physical and geometric attributes. As annotated data for object parts and physics are rare, we propose a novel formulation that learns physical primitives by explaining both an object's appearance and its behaviors in physical events. Our model performs well on block towers and tools in both synthetic and real scenarios; we also demonstrate that visual and physical observations often provide complementary signals. We further present ablation and behavioral studies to better understand our model and contrast it with human performance.
 </p>
 <hr>
</details>

### 2017
<details>
 <summary><b>3D-PRNN: Generating Shape Primitives with Recurrent Neural Networks</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Primitives/3D-PRNN.md">[Paper Note]</a></summary>
 <hr>
 <p align="justify">
The success of various applications including robotics, digital content creation, and visualization demand a structured and abstract representation of the 3D world from limited sensor data. Inspired by the nature of human perception of 3D shapes as a collection of simple parts, we explore such an abstract shape representation based on primitives. Given a single depth image of an object, we present 3DPRNN, a generative recurrent neural network that synthesizes multiple plausible shapes composed of a set of primitives. Our generative model encodes symmetry characteristics of common man-made objects, preserves long-range structural coherence, and describes objects of varying complexity with a compact representation. We also propose a method based on Gaussian Fields to generate a large scale dataset of primitive-based shape representations to train our network. We evaluate our approach on a wide range of examples and show that it outperforms nearest-neighbor based shape retrieval methods and is on-par with voxelbased generative models while using a significantly reduced parameter space.
 </p>
 <hr>
</details>

<details>
 <summary><b>Learning Shape Abstractions by Assemling Volumetric Primitives</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Primitives/LSAAVP.md">[Paper Note]</a></summary>
 <hr>
 <p align="justify">
We present a learning framework for abstracting complex shapes by learning to assemble objects using 3D volumetric primitives. In addition to generating simple and geometrically interpretable explanations of 3D objects, our framework also allows us to automatically discover and exploit consistent structure in the data. We demonstrate that using our method allows predicting shape representations which can be leveraged for obtaining a consistent parsing across the instances of a shape collection and constructing an interpretable shape similarity measure. We also examine applications for image-based prediction as well as shape manipulation.
 </p>
 <hr>
</details>

## Voxels
### 2018
<details>
 <summary><b>FeatureNet: Machining Feature Recognition Based on 3D Convolution Neural Network</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Voxels/FeatureNet.md">[Paper Note]</a></summary>
 <hr>
 <p align="justify">
Automated machining feature recognition, a sub-discipline of solid modeling, has been an active research area for last three decades and is a critical component in digital manufacturing thread for detecting manufacturing information from computer aided design (CAD) models. In this paper, a novel framework using Deep 3D Convolutional Neural Networks (3D-CNNs) termed FeatureNet to learn machining features from CAD models of mechanical parts is presented. FeatureNet learns the distribution of complex manufacturing feature shapes across a large 3D model dataset and discovers distinguishing features that help in recognition process automatically. To train FeatureNet, a large-scale mechanical part datasets of 3D CAD models with labeled machining features is automatically constructed. The proposed framework can recognize manufacturing features from the low-level geometric data such as voxels with a very high accuracy. The developed framework can also recognize planar intersecting features in the 3D CAD models. Extensive numerical experiments show that FeatureNet enables significant improvements over the state-of-the-arts manufacturing feature detection techniques. The developed data-driven framework can easily be extended to identify a large variety of machining features leading to a sound foundation for real-time computer aided process planning (CAPP) systems.
 </p>
 <hr>
</details>

<details>
 <summary><b>Learning localized features in 3D CAD models for manufacturability analysis of drilled holes</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Voxels/DLDFM.md">[Paper Note]</a></summary>
 <hr>
 <p align="justify">
We present a novel feature identification framework to recognize difficult-to-manufacture drilled holes in a complex CAD geometry using deep learning. Deep learning algorithms have been successfully used in object recognition, video analytics, image segmentation, etc. Specifically, 3D Convolutional Neural Networks (3D-CNNs) have been used for object recognition from 3D voxel data based on the external shape of an object. On the other hand, manufacturability of a component depends on local features more than the external shape. Learning these local features from a boundary representation (B-Rep) CAD model is challenging due to lack of volumetric information. In this paper, we learn local features from a voxelized representation of a CAD model and classify its manufacturability. Further, to enable effective learning of localized features, we augment the voxel data with surface normals of the object boundary. We train a 3D-CNN with this augmented data to identify local features and classify the manufacturability. However, this classification does not provide information about the source of non-manufacturability in a complex component. Therefore, we have developed a 3D-CNN based gradient-weighted class activation mapping (3D-GradCAM) method that can provide visual explanations of the local geometric features of interest within an object. Using 3D-GradCAM, our framework can identify difficult-to-manufacture features, which allows a designer to modify the component based on its manufacturability and thus improve the design process. We extend this framework to identify difficult-to-manufacture features in a realistic CAD model with multiple drilled holes, which can ultimately enable development of a real-time manufacturability decision support system.
  </p>
 <hr>
</details>

### 2017
<details>
 <summary><b>Generative and Discriminative Voxel Modeling with Convolutional Neural Networks</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Voxels/VRN.md">[Paper Note]</a></summary>
 <hr>
 <p align="justify">
When working with three-dimensional data, choice of representation is key. We explore voxel-based models, and present evidence for the viability of voxellated representations in applications including shape modeling and object classification. Our key contributions are methods for training voxel-based variational autoencoders, a user interface for exploring the latent space learned by the autoencoder, and a deep convolutional neural network architecture for object classification. We address challenges unique to voxel-based representations, and empirically evaluate our models on the ModelNet benchmark, where we demonstrate a 51.5% relative improvement in the state of the art for object classification.
 <hr>
 </p>
</details>

<details>
 <summary><b>Orientation-boosted Voxel Nets for 3D Object Recognition</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Voxels/ORION.md">[Paper Note]</a></summary>
 <hr>
 <p align="justify">
Recent work has shown good recognition results in 3D object recognition using 3D convolutional networks. In this paper, we show that the object orientation plays an important role in 3D recognition. More specifically, we argue that objects induce different features in the network under rotation. Thus, we approach the category-level classification task as a multi-task problem, in which the network is trained to predict the pose of the object in addition to the class label as a parallel task. We show that this yields significant improvements in the classification results. We test our suggested architecture on several datasets representing various 3D data sources: LiDAR data, CAD models, and RGB-D images. We report state-of-the-art results on classification as well as significant improvements in precision and speed over the baseline on 3D detection. 
 <hr>
 </p>
</details>

### 2015
<details>
 <summary><b>3D ShapeNets: A Deep Representation for Volumetric Shapes</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Voxels/ShapeNet.md">[Paper Note]</a></summary>
 <hr>
 <p align="justify">
3D shape is a crucial but heavily underutilized cue in today’s computer vision systems, mostly due to the lack of a good generic shape representation. With the recent availability of inexpensive 2.5D depth sensors (e.g. Microsoft Kinect), it is becoming increasingly important to have a powerful 3D shape representation in the loop. Apart from category recognition, recovering full 3D shapes from viewbased 2.5D depth maps is also a critical part of visual understanding. To this end, we propose to represent a geometric 3D shape as a probability distribution of binary variables on a 3D voxel grid, using a Convolutional Deep Belief Network. Our model, 3D ShapeNets, learns the distribution of complex 3D shapes across different object categories and arbitrary poses from raw CAD data, and discovers hierarchical compositional part representation automatically. It naturally supports joint object recognition and shape completion from 2.5D depth maps, and it enables active object recognition through view planning. To train our 3D deep learning model, we construct ModelNet – a largescale 3D CAD model dataset. Extensive experiments show that our 3D deep representation enables significant performance improvement over thestateofthearts in a variety of tasks.
 <hr>
 </p>
</details>

<details>
 <summary><b>VoxNet: A 3D Convolutional Neural Network for Real-Time Object Recognition</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Voxels/VoxNet.md">[Paper Note]</a></summary>
 <hr>
 <p align="justify">
Robust object recognition is a crucial skill for robots operating autonomously in real world environments. Range sensors such as LiDAR and RGBD cameras are increasingly found in modern robotic systems, providing a rich source of 3D information that can aid in this task. However, many current systems do not fully utilize this information and have trouble efficiently dealing with large amounts of point cloud data. In this paper, we propose VoxNet, an architecture to tackle this problem by integrating a volumetric Occupancy Grid representation with a supervised 3D Convolutional Neural Network (3D CNN). We evaluate our approach on publicly available benchmarks using LiDAR, RGBD, and CAD data. VoxNet achieves accuracy beyond the state of the art while labeling hundreds of instances per second.
 <hr>
 </p>
</details>
      
<hr>

# Other Machine Learning Papers
## Networks
### 2015
<details>
 <summary><b>Deep Residual Learning for Image Recognition</b> <a href="https://github.com/AndrewColligan/Paper-Reading-Notes/blob/master/Notes/Other_Machine_Learning_Papers/ResNet.md">[Paper Note]</a></summary>
<hr>
 <p align="justify">
Deeper neural networks are more difficult to train. We present a residual learning framework to ease the training of networks that are substantially deeper than those used previously. We explicitly reformulate the layers as learning residual functions with reference to the layer inputs, instead of learning unreferenced functions. We provide comprehensive empirical evidence showing that these residual networks are easier to optimize, and can gain accuracy from considerably increased depth. On the ImageNet dataset we evaluate residual nets with a depth of up to 152 layers—8 deeper than VGG nets [41] but still having lower complexity. An ensemble of these residual nets achieves 3.57% error on the ImageNet test set. This result won the 1st place on the ILSVRC 2015 classification task. We also present analysis on CIFAR-10 with 100 and 1000 layers. The depth of representations is of central importance for many visual recognition tasks. Solely due to our extremely deep representations, we obtain a 28% relative improvement on the COCO object detection dataset. Deep residual nets are foundations of our submissions to ILSVRC & COCO 2015 competitions1, where we also won the 1st places on the tasks of ImageNet detection, ImageNet localization, COCO detection, and COCO segmentation.
</p>
<hr>
</details>

<hr>
<sub><sup>Paper Count: 26</sup></sub>
