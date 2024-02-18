directory 

 concept 

 Point cloud segmentation 

 Point cloud classification 

  feature extraction 

 split 

 object recognition 

 classification 

  Common point cloud segmentation methods 

 Random sample consensus algorithm (Random Sample Consensus, RANSAC) 

 algorithm flow 

  The difference between RANSAC and least squares 

  Sample_consensus modules in PCL 

  European clustering segmentation (clustering) 

 Region growth algorithm (clustering) 

 Color-based region growth segmentation (clustering) 

  Segmentation of Minimum Graph Cut 

 Segmentation Based on Normal Differentiation 

  segmentation based on hypervoxel 

  Deep learning segmentation method 

#  concept 

##  Point cloud segmentation 

 According to the spatial, geometric and textural feature points, the point clouds in the same partition have similar features. 

 The purpose of point cloud segmentation is to divide into chunks, thus facilitating individual processing. 

##  Point cloud classification 

 Assign a semantic tag to each point. Point cloud classification is the classification of point clouds into different point clusters. The same point cloud has similar or identical properties, such as ground, trees, people, etc. Also known as point cloud semantic segmentation. 

 ![avatar]( 2021090513320634.png) 

##   feature extraction 

 A single point or a group of points can be detected based on a certain type of point. 

##  split 

 The process of grouping points into a section or an object based on the above low-level properties. The further processing and analysis of each object by the segmentation process makes it more informative than processing or analyzing each point individually. 

##  object recognition 

 The process of identifying one or more types of objects in a point cloud. This process is usually performed by performing analysis based on the results of feature extraction and segmentation, and based on prior knowledge under given constraints and rules. 

##  classification 

 Similar to the process of object recognition, this process assigns a category or identifier to each point, line segment, or object to represent certain types of objects (e.g., signs, roads, markers, or buildings). 

 The difference between object recognition and point cloud classification is that: 

 The effective segmentation of point clouds is a prerequisite for many applications. 

#   Common point cloud segmentation methods 

##  Random sample consensus algorithm (Random Sample Consensus, RANSAC) 

 The parameters of the mathematical model are estimated iteratively from a set of observed data containing outliers. 

 The RANSAC algorithm assumes that the data contains both correct and abnormal data (or noise). 

 The correct data is recorded as inliers, and the abnormal data is recorded as outliers. 

 At the same time, RANSAC also assumes that given a set of correct data, there is a way to calculate the model parameters that match these data. The core idea of the algorithm is randomness and hypothesis: 

 RANSAC algorithm is widely used in the field of computer vision and mathematics, such as line fitting, plane fitting, computing the transformation matrix between images or point clouds, computing the basic matrix and so on. 

 Although the basic detection algorithm based on RANSAC has high robustness and efficiency, it is currently only suitable for the basic primitive of plane, sphere, cylinder, cone and ring species. 

###  algorithm flow 

 ![avatar]( 20210905140905521.png) 

>  Martin A. Fischler 和Robert C. Bolles于1981年发表在ACM期刊上的论文《Random Sample Consensus: A Paradigm for Model Fitting with Applications to Image Analysis and Automated Cartography》 

###   The difference between RANSAC and least squares 

  The least squares method tries to adapt to all points, including outliers. In contrast, RANSAC can come up with a model that is calculated using only the outliers, and the probability is high enough. However, RANSAC does not guarantee that the result will be correct. In order to ensure that the algorithm has a high enough reasonable probability, the parameters of the algorithm must be carefully selected (parameter configuration). After experimental verification, the effect of RANSAC is much better than that of the direct least squares method for datasets containing 80% error. 

  The most important parameter is the number of iterations k: 

 ![avatar]( 20210905150339330.png) 

 ![avatar]( 2021090515040982.png) 

 ![avatar]( 2021090515042636.png) 

###   Sample_consensus modules in PCL 

  The Sample_consensus library in PCL implements random sampling consistency and its generalization estimation algorithm, as well as various common geometric models such as plane and cylinder. Different estimation algorithms and different geometric models are freely combined to estimate the coefficients of specific geometric models implied in point clouds, and realize the segmentation of geometric models located in point clouds. 

 The following models are supported: 

>  SACMODEL_PLANE - Used to determine a plane model. Four coefficients of a plane. SACMODEL_LINE - Used to determine a line model. Six coefficients of a line are given by a point on the line and the direction of the line. SACMODEL_CIRCLE2D - Used to determine a 2D circle in a plane. Three coefficients of a circle are given by its center and radius. SACMODEL_CIRCLE3D - Used to determine a 3D circle in a plane. Seven coefficients of a circle are given by its center, radius and normal. SACMODEL_SPHERE - Used to determine a sphere model. Four coefficients of a sphere are given by its 3D center and radius. SACMODEL_CYLINDER - Used to determine a cylinder model. Seven coefficients of a cylinder are given by points on its axis, axial direction and radius. SACMODEL_CONE - Used to determine a cone model. The seven coefficients of a cone are given by its vertex, axis direction and opening angle. SACMODEL_TORUS - Not yet implemented SACMODEL_PARALLEL_LINE - Model to determine a line parallel to a given axis within the maximum specified angular deviation. Linear coefficients are similar to SACMODEL_LINE. SACMODEL_PERPENDICULAR_PLANE - Model to determine a plane perpendicular to a user specified axis within the maximum specified angular deviation. Planar coefficients are similar to SACMODEL_PLANE. SACMODEL_PARALLEL_LINES - Not yet implemented

SACMODEL_NORMAL_PLANE - A model that determines a plane model using additional constraints: The surface normal of each interior point must be parallel to the surface normal of the output plane, within the specified maximum angular deviation. The plane coefficients are similar to SACMODEL_PLANE. SACMODEL_NORMAL_SPHERE - Similar to SACMODEL_SPHERE, but with additional surface normal constraints. SACMODEL_PARALLEL_PLANE - A model that determines a plane that is parallel to the user-specified axis, within the maximum specified angular deviation. The plane coefficients are similar to SACMODEL_PLANE. SACMODEL_NORMAL_PARALLEL_PLANE A 3D plane segmentation model is defined using additional surface normal constraints. The plane normals must be parallel to the user-specified axis. Therefore, SACMODEL_NORMAL_PARALLEL_PLANE equivalent to SACMODEL_NORMAL_PLANE + SACMODEL_PERPENDICULAR_PLANE. The plane coefficients are similar to SACMODEL_PLANE. SACMODEL_STICK - A 3D rod segmentation model. A stick is a line of minimum/maximum width for a given user. 

 The following list describes the implementation of a robust sample consensus estimator: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957379146
  ```  
 ![avatar]( 20210905152446574.png) 

 ![avatar]( 20210905152451681.png) 

>  Schnabel R, Wahl R, Klein R. Efficient RANSAC for point‐cloud shape detection[C]//Computer graphics forum. Oxford, UK: Blackwell Publishing Ltd, 2007, 26(2): 214-226.

https://cg.cs.uni-bonn.de/en/publications/paper-details/schnabel-2007-efficient/ 

##   European clustering segmentation (clustering) 

 Clustering method to determine the degree of closeness between points through feature space 

 Algorithm flow: 

 ![avatar]( 20210905153204769.png) 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957379146
  ```  
  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957379146
  ```  
 The setting of this condition can be customized by us, because in addition to the distance check, the clustered points also need to meet a special custom requirement, that is, the first point is used as the seed point, and the candidate points around it are used as its comparison or comparison objects. If the conditions are met, they will be added to the clustered objects. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957379146
  ```  
##  Region growth algorithm (clustering) 

 Region growth algorithm: gather similar point clouds to form a region. First, find a seed point for each region to be divided as the starting point for growth, and then merge the points in the neighborhood around the seed point with the same or similar properties as the seed into the area where the seed pixel is located. And the new point continues to grow around as a seed until no more pixels can be included in the condition, and an area grows. 

 Algorithm flow: 

 ![avatar]( 20210905154033491.png) 

  The algorithm is designed for the small curvature change surface, especially for the segmentation of the continuous step plane. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957379146
  ```  
##  Color-based region growth segmentation (clustering) 

 Color-based region growth segmentation 

 The color-based region growth segmentation method is the same in principle as the segmentation method based on curvature and normals, but the comparison target is changed to color. It can be considered that the same color and close to each other are very likely to be the same type, and it is more suitable for indoor scene segmentation. Especially in complex indoor scenes, color segmentation can easily turn continuous scene point clouds into different objects. Even if it is uneven ground, try to use the sampled uniform splitter to remove the plane, and the color segmentation algorithm can achieve segmentation of objects of different colors. 

 ![avatar]( 20210905154324965.png) 

 The algorithm is mainly divided into two steps: 

  RBG distance 

 ![avatar]( 20210905154438203.png) 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957379146
  ```  
##   Segmentation of Minimum Graph Cut 

 The min-cut in graph theory is widely used in network programming, solving bridge problems, image segmentation and other fields. 

 The minimum cut algorithm is a concept in graph theory. Its function is to separate two points in some way. Of course, the two points may be reconnected by countless points. If you want to separate the leftmost point and the rightmost point, both red and green cuts are possible, but from the number of lines crossed, you can draw the conclusion that the green line is the better cutting method. 

 ![avatar]( 20210905155004755.jpg) 

 ![avatar]( 20210905155734967.jpg) 

>  http://gfx.cs.princeton.edu/pubs/Golovinskiy_2009_MBS/paper_small.pdf 

 The main idea of the algorithm: 

 ![avatar]( 20210905155916221.png) 

 Here dist is the distance between the points. The further away from the points, the more likely the edges are to be cut. 

         3. The algorithm sets the data cost. It includes foreground and background penalties. The first is the weight of the edge that connects the cloud point to the source vertex and has a user-defined constant value. 

 ![avatar]( 20210905160242957.png) 

  Divide the former scenic spot and the back scenic spot of the point cloud. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957379146
  ```  
##  Segmentation Based on Normal Differentiation 

 According to the difference of normal vector features at different scales, using PCL :: DifferenceOfNormalsEstimation to realize point cloud segmentation, the point cloud segmentation effect is better in dealing with scenes with large scale changes, using different support radii to estimate two unit normal vectors of the same point, the difference of unit normal vector defines the DoN feature 

 DoN algorithm: 

 The DoN feature is derived from the observation that the surface normal vector based on the given radius can reflect the intrinsic geometric characteristics of the surface. Therefore, this segmentation algorithm is based on normal estimation, and needs to calculate the normal estimation of a certain point in the point cloud. Neighborhood information is usually used in the calculation of normal estimation, and it is obvious that the choice of neighborhood size will affect the result of normal estimation. 

 In the DoN algorithm, the size of the neighborhood selection is called the support radius. If you choose a different support radius for a point in the point cloud, you can get different normal estimates, and the difference between the normals is the normal difference. 

 ![avatar]( 20210905160742405.png) 

>  PCL_ Point Cloud Segmentation _ Differential Segmentation Based on Normal 

 Algorithm flow: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957379146
  ```  
 ![avatar]( 20210905161718818.png) 

 ![avatar]( 20210905161728256.png) 

>  Difference of Normals as a Multi-Scale Operator in Unorganized Point Clouds 

##   segmentation based on hypervoxel 

  A super voxel is a set of elements that are "voxels". Similar to the volume in a voxel filter, its essence is small squares one by one. Unlike all the segmentation methods mentioned earlier, the purpose of super voxel clustering is not to segment a specific object. It performs over segmentation on the point cloud, breaking the scene point cloud into many small pieces, and studying the relationship between each small piece. The point cloud is divided by an octree to obtain the adjacency relationship between different point clusters. Similar to the image, there are many adjacency relationships of point clouds, such as surface, adjacency, line adjacency, and point adjacency. 

 ![avatar]( 20210905162024660.png) 

>  [PCL] - Detailed explanation of superbody clustering point cloud segmentation algorithm 

  Superbody clustering is actually a special region growth algorithm. Unlike unlimited growth, superbody clustering first requires a regular arrangement of regions to grow "nuclei". The nuclei are actually uniformly distributed in space, and the nucleus distance (Rseed) is specified, the particle distance (Rvoxel) is specified, and the minimum grain (MOV) is specified. 

 ![avatar]( 20210905162213646.png) 

  After we have the grain and crystal range, we only need to control the crystallization process to divide the entire space. The essence of the crystallization process is to continuously absorb similar particles (octave space). Similar is a relatively vague concept, and there is the following formula for the definition of similar: 

 ![avatar]( 20210905162236984.png) 

 Dc in the formula represents the difference in color, Dn represents the difference on the normal line, and Ds represents the difference in point distance. W represents a series of weights that are used to control the crystal shape. Look for a circle around the crystal nucleus, and the smallest voxel of D is considered the next "object to be developed". 

 It is important to note that the crystallization process is not to grow one crystal nucleus and then the next, but to start growing at the same time. Then all crystal nuclei continue to compete fairly and develop a second "object", in this cycle. Eventually, all crystals should complete growth almost simultaneously, and the entire point cloud is also divided by the crystal lattice, ensuring that the particles in a crystal bag are all similar. 

 ![avatar]( 20210905162424814.png) 

 ![avatar]( 20210905162436169.png) 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957379146
  ```  
##   Deep learning segmentation method 

 Deep learning is currently the most influential and fastest-growing cutting-edge technology in pattern recognition, computer vision, and data analytics. 

 ![avatar]( 20210905162636146.png) 

  1. Based on multiple views 

  2. Voxel-based 

 ![avatar]( 20210905162659879.png) 

  3. End-to-end - processing point clouds directly 

 ![avatar]( 20210905162715179.png) 

 ![avatar]( 20210905162722291.png) 

>  Guo Y, Wang H, Hu Q, et al. Deep learning for 3d point clouds: A survey[J]. IEEE transactions on pattern analysis and machine intelligence, 2020. 

 ![avatar]( 20210905162753520.png) 

>  Guo Y, Wang H, Hu Q, et al. Deep learning for 3d point clouds: A survey[J]. IEEE transactions on pattern analysis and machine intelligence, 2020. 

