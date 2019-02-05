# Datasets

## ModelNet

### Description
The goal of the Princeton ModelNet project is to provide researchers in computer vision, computer graphics, robotics and cognitive science, with a comprehensive clean collection of 3D CAD models for objects. 
To build the core of the dataset, we compiled a list of the most common object categories in the world, using the statistics obtained from the SUN database. 
Once we established a vocabulary for objects, we collected 3D CAD models belonging to each object category using online search engines by querying for each object category term. 
Then, we hired human workers on Amazon Mechanical Turk to manually decide whether each CAD model belongs to the specified cateogries, using our in-house designed tool with quality control. 
To obtain a very clean dataset, we choose 10 popular object categories, and manually deleted the models that did not belong to these categories. 
Furthermore, we manually aligned the orientation of the CAD models for this 10-class subset as well. 
We provide both the 10-class subset and the full dataset for download.

### ModelNet10
Dataset containing CAD models from 10 categories.

### ModelNet40
Dataset containing CAD models from 40 categories.

| Algorithm        | Input        | ModelNet40 Classification | ModelNet40 Retrieval | ModelNet10 Classification | ModelNet10 Retrieval |  
| ---------------- | ------------ |        ---------          |        ---------     |      ---------            |       ---------      |
| 3DShapeNet       | volumetric   | 77.3%                     | 49.2%                | 83.5%                     | 68.3%                |
| FusionNet        | vol + mul    | 90.8%                     |                      | 93.11%                    |                      |
| MVCNN            | multi-view   | 90.1%                     | 79.5%                |                           |                      |
| PointNet         | points       |                           |                      | 77.6%                     |                      |
| VoxNet           | volumetric   | 83%                       |                      | 92%                       |                      |
| NormalNet        | vol + norm   | 88.8%                     |                      | 93.1                      |                      |

### Link
http://modelnet.cs.princeton.edu/
