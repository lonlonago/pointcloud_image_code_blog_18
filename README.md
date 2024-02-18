![avatar]( b24b677a4d464a909112588c6cbddb3c.png) 

#  I. Basic information 

 The SensatUrban dataset is a city-scale photogrammetry point cloud dataset proposed by Qingyong Hu (RandLANet) team for the field of 3D scene understanding. 

 The data collection uses the fixed-wing drone Ebee X to acquire high-precision, high-resolution aerial images, and then uses off-the-shelf software such as Pix4D based on Structure from Motion (SfM) and dense image matching to reconstruct dense and colorful 3D point clouds from captured aerial image sequences. 

 For the urban area around Birmingham, all captured successive images were fed into Pix4D, generating a total of 569,147,075 3D points covering an area of 1.6 square kilometers. Similarly, the urban area near Cambridge was redeveloped with 2,278,514,725 points covering an area of approximately 4.6 square kilometers. In addition, 904,155,619 points within 3.2 square kilometers were also collected in Yorkshire. 

 ![avatar]( c66dee5824224d3b9a8403247ec8afa9.png) 

#  Ii. data analytics 

 The SensatUrban dataset contains nearly 3 billion of 7.6 square kilometers of points in three UK cities (Birmingham, Cambridge, and York) with detailed semantic annotations. Sample graphs are as follows 

 ![avatar]( 6f91a38b33074b30b07fdb31edbb62bf.png) 

 Category: 

 At the same time, the author divides the data when using this dataset for training. Similar to the DALES dataset, the author divides the point cloud of each area into a series of point cloud blocks of similar size to ensure that it can be input into the existing GPU for training and testing. The point cloud in the Birmingham urban area is divided into 14 blocks, and 10 of them are selected as the training dataset, 2 as the validation set, and 2 as the test set. Similarly, the Cambridge area is divided into 29 blocks, of which 20 are used as the training dataset, 5 as the validation set, and the remaining 4 as the test set. Each point cloud block is about 400 × 400 square meters. The specific category distribution of the data is shown in the figure below: 

 ![avatar]( d0f47a0735d8480c90fa16bb4f445390.png) 

#  Data download 

 dataset_release.zip 

#  reference 

 1、[CVPR 2021] SensatUrban:城市规模点云数据集 2、Towards Semantic Segmentation of Urban-Scale 3D Point Clouds: A Dataset, Benchmarks and Challenges 



--------------------------------------------------------------------------------

PCL (Point Cloud Library) is a large cross-platform open-source C++ programming library established on the basis of absorbing previous research on point clouds. It realizes a large number of general algorithms and efficient data structures related to point clouds, involving point cloud acquisition, filtering, segmentation, registration, retrieval, feature extraction, recognition, tracking, surface reconstruction, visualization, etc. It supports a variety of operating system platforms and can run on Windows, Linux, Android, Mac OS X, and some embedded real-time systems. If OpenCV is the crystallization of 2D information acquisition and processing, then PCL has the same status in 3D information acquisition and processing. PCL is a BSD authorization method and can be used for commercial and academic applications for free 

 ![avatar]( aHR0cDovL2ltZy5ibG9nLmNzZG4ubmV0LzIwMTcxMjA2MTAyOTI5OTU5) 

 Ubuntu under the PCL official installation method is: sudo add-apt-repository ppa: v-launchpad-jochen-sprickerhof-de/pcl sudo apt-get update sudo apt-get install libpcl-all is very simple, then the Python PCL library installation is also a tutorial, but compared to the C++ library is relatively small, the routine is relatively small, so, today will not demonstrate, the operation of interested students can query the URL https://github.com/strawlab/python-pcl 

 https://www.quora.com/How-do-I-install-PCL-for-Python-in-Windows operation, the specific instructions are as follows: Introduction 

 This is a small python binding to the pointcloud library. Currently, the following parts of the API are wrapped (all methods operate on PointXYZ) point types 

 I/O and integration; saving and loading PCD files segmentation SAC smoothing filtering registration (ICP, GICP, ICP_NL) 

 The code tries to follow the Point Cloud API, and also provides helper function for interacting with NumPy. For example (from tests/test.py) 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573747740
  ```  
 or, for smoothing 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573747740
  ```  
 Point clouds can be viewed as NumPy arrays, so modifying them is possible using all the familiar NumPy functionality: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573747740
  ```  
 More samples can be found in the examples directory, and in the unit tests. 

 This work was supported by Strawlab. 

 Requirements 

 This release has been tested on Linux Ubuntu 14.04 with 

 Python 2.7.6, 3.4.0, 3.5.2 pcl 1.7.0 Cython <= 0.25.2 and MacOS with 

 Python 2.7.6, 3.4.0, 3.5.2 pcl 1.8.1(use homebrew) Cython <= 0.25.2 and Windows with 

 (Miniconda/Anaconda) - Python 3.4 pcl 1.6.0(VS2010) Cython <= 0.25.2 Gtk+ and Windows with 

 (Miniconda/Anaconda) - Python 3.5 pcl 1.8.0(VS2015) Cython <= 0.25.2 Gtk+ Installation 

 Linux (Ubuntu) 

 PCL 1.7.0(use apt-get) 

 Install PCL Module. sudo add-apt-repository ppa:v-launchpad-jochen-sprickerhof-de/pcl -y 

 sudo apt-get updated -and 

 sudo apt-get install libpcl-all -y PCL 1.8.0 (build module)([CI Test Timeout]) 

 Build Module 

 Reference here. MacOSX 

 use homebrew 

 Install PCL Module. brew tap homebrew/science 

 brew install pcl Warning: 

 Current Installer (2017/10/02) Not generated pcl-2d-1.8.pc file.(Issue #119) 

 Reference PointCloudLibrary Issue. 

 Pull qequests 1679. 

 Issue 1978. circumvent: 

 copy travis/pcl-2d-1.8.pc file to /usr/local/lib/pkgconfig folder. Windows 

 before Install module 

 Case1. use PCL 1.6.0 

 Windows SDK 7.1 PCL All-In-One Installer 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573747740
  ```  
 Common setting 

 pip module install. pip install --upgrade pip 

 pip install cython = =0.25.2 

 pip install numpy instal python module python setup.py build_ext -i 

 python setup.py install Build & Test Status 

 windows(1.6.0/1.8.1) 

 Mac OSX (1.8.1)/Ubuntu14.04 (1.7.0) 

 A note about types 

 Point Cloud is a heavily templated API, and consequently mapping this into Python using Cython is challenging. 

 It is written in Cython, and implements enough hard bits of the API (from Cythons perspective, i.e the template/smart_ptr bits) to provide a foundation for someone wishing to carry on. 

 API Documentation 

 For deficiencies in this documentation, please consult the PCL API docs, and the PCL tutorials. 

 The above is the information I have integrated, so installing the Python PCL library is very simple, but there are relatively few routines. If you are interested, you can study it yourself. If you have any friends who study Python at the same time, please share it actively. Follow the WeChat official account, or join the QQ group to communicate and share! 



--------------------------------------------------------------------------------

#  overview 

 Common point cloud registration is a single registration, the most classic is coarse + icp fine registration. This paper uses hough to identify according to the cg algorithm in PCL. 

#  algorithm flow 

 1. Calculate normal 2. Uniform downsampling 3. Shot descriptor 4. Find correspondence 5. Use hough for registration 

#  process 

 ![avatar]( c889dea82ac9416ba55d9292a8bb6fee.png) 

 1. The original point cloud is as follows (Note: The point cloud data comes from Pengli 3D camera) 2. Registration display:  

 ![avatar]( 45cd51e7ba0441d8b2ed501ee61b7c66.png) 

 3. Registration result: green is the template point cloud, red is the registered point cloud, and blue is the sampled template and scene point cloud. 3. Registration matrix Instance 1 -0.954096 0.268854 -0.131979 143.093 -0.249819 -0.957457 -0.144453 312.399 -0.165201 -0.104852 0.980671 -23.7059 0 0 1 

 Instance 2 -0.991586 -0.0764673 -0.10445 315.292 0.0794278 -0.99654 -0.0244786 118.135 -0.102216 -0.0325689 0.994229 -61.2683 0 0 0 1 

 Instance 3 -0.998138 -0.0601465 0.0101171 310.928 0.0604276 -0.997714 0.030263 56.9239 0.0082738 0.030818 0.999491 -99.1217 0 0 0 1 

 Instance 4 -0.999558 -0.0199898 0.0220236 421.992 0.0200465 -0.999796 0.00236082 95.5149 0.021972 0.00280128 0.999755 -93.8967 0 0 0 1 

 Instance 5 -0.974308 -0.0302755 -0.223178 838.464 0.0247241 -0.999312 0.0276273 62.7956 -0.223861 0.0213997 0.974386 -14.9758 0 0 0 1 

 Instance 6 0.995402 -0.0953485 -0.00915375 -26.4745 0.0919225 0.977743 -0.188599 71.0808 0.0269327 0.186891 0.982011 -106.315 0 0 0 1 

 Instance 7 0.993101 0.0247692 -0.11462 204.98 -0.0205901 0.999084 0.0375023 -185.268 0.115444 -0.0348835 0.992701 -87.0265 0 0 0 1 

 Instance 8 0.961276 0.185717 0.203613 -589.633 -0.15904 0.977225 -0.140493 61.6279 -0.225068 0.10267 0.968919 -37.016 0 0 0 1 

 Instance 9 0.997246 0.0271222 0.0690321 -274.307 -0.0308815 0.998064 0.0539868 -195.472 -0.0674343 -0.05597 0.996153 -61.2137 0 0 0 1 

 Instance 10 -0.980549 -0.179777 -0.0787599 828.43 0.185432 -0.980049 -0.0715434 141.976 -0.0643267 -0.0847565 0.994323 -47.6181 0 0 0 1 

 Instance 11 0.993726 0.0035918 0.111787 74.8284 -0.00202689 0.999898 -0.0141095 -132.863 -0.111826 0.0137944 0.993632 -56.3289 0 0 0 1 

 Instance 12 0.995317 -0.0547616 0.0796628 252.42 0.0618801 0.994034 -0.0898222 -53.1371 -0.0742687 0.0943311 0.992767 -71.2469 0 0 0 1 

#  conclusion 

 For the 12 targets of the point cloud in the above scene, all recognition can be carried out using this method. Time consumption: 16s, with an average of 1.35s for each target. Error: As can be seen from the picture, the individual registration accuracy is not high, and it can be operated through subsequent optimization. 



--------------------------------------------------------------------------------

#  I. Introduction 

 A few days ago, I took the time to run the common reconstruction methods in PCL and CGAL, and I will summarize them here today. 

 First, the main methods: 

 II. Data: 

 Take bunny data as an example to show the reconstruction effect  

#  Effect display 

##  2.1 Implemented in PCL 

 1. Convex hull reconstruction 

 ![avatar]( 66890e80133f4857a01ebabe48713e2f.png) 

 2. Concave bag reconstruction 

 ![avatar]( a7ea9a19a24540e2b73084ecaa0e6648.png) 

 Alpha=0.5  

 ![avatar]( ceaebe14915a475f837faf3838a701ac.png) 

 Alpha=1.5  Alpha=5  

 ![avatar]( 4a95ea0a406747b4ad41cb41c09e5586.png) 

 Alpha=15  

 3. Greedy reconstruction 

 ![avatar]( e520290204214407962b9863f4865912.png) 

 4. Poisson Reconstruction 

 ![avatar]( 244fbd3c0e7c45dabd535c2abb66ea7e.png) 

##  2.2 Implementation in CGAL 

 1. The reconstruction process in CGAL is as follows 

 ![avatar]( 6442e2f65d504b1fbdcfba3e5aa2db07.png) 

  2. Reconstruction effect in CGAL 

 ![avatar]( 5acc590088694472a23d9de2cb01a527.png) 

 ![avatar]( 02c448eda527447ba2a9ee296187c491.png) 

 ![avatar]( 9cda6bfe9a1346c88baecefb8e2f7053.png) 

#  III. Follow-up 

 The code will be released or integrated into QT + PCL later. 



--------------------------------------------------------------------------------

#  Comparison of Several Point Cloud Registration Algorithms 

 Refer to many blogs, read a lot of algorithms for point cloud registration, decided to make a summary of point cloud registration these days, mainly to prevent yourself from forgetting. Mainly refer to the following blog, the link has been attached. https://blog.csdn.net/peach_blossom/article/details/78506184 

##  Algorithm implementation software and hardware environment 

 CPU：intel corei5-5200 @2.20Hz 

 sentire:Nvidia GeForce GTX 850M 

 Memory: 8GB 

 Operating System: Windows 10 Professional 

 Development environment: Vs2013 + pcl1.8.0 (release) 

 Point cloud registration dataset: bunny rabbits from different angles 

##  Second, point cloud registration comparison 

 2.1 Register the target. According to the original point cloud and the target point cloud, the transformation matrix, namely the rotation matrix R and the translation matrix T, is obtained by registration, and the error is calculated to compare the matching results. There are mainly the following comparisons: (1) based on local feature descriptors (PFH, FPFH, 3Dsc); (2) based on probability distribution (NDT); (3) ICP rough registration comparison. 

 2.2 Registration target (1) Extraction of key points (2) Feature description (3) Consistency estimation (4) Fine registration (5) Error analysis: There is a point cloud, and the target point cloud is obtained by continuously rotating the transformation. After that, the following registration methods are used to obtain R and T, and the actual transformation matrix is compared to obtain the error. 

 2.3 Comparison of rough registration, the principles of various algorithms for rough registration are not introduced, and many blogs have given detailed explanations. In registration, due to the characteristics of different point cloud datasets, different key points need to be extracted. This paper uniformly filters and samples the dataset to reduce the number of points to improve the efficiency of the algorithm. 

 ![avatar]( 20190305162728498.png) 

 2.3.1 result graph analysis, the original figure pfh rough registration fpfh rough registration 3Dsc rough registration ndt rough registration  

 2.3.2 time analysis 

 ![avatar]( 20190305163237134.png) 

 2.3.3 transformation matrix analysis, the transformation matrix structure is 

 ![avatar]( 20190305163651579.png) 

 ![avatar]( 20190305164331364.png) 

 2.3.4 error analysis  

 2.4 ICP usage in rough registration 

 ![avatar]( 20190305164512461.png) 

 ![avatar]( 20190305164524928.png) 

 ICP registration is generally used in fine registration. I read the online blog and it seems that it can be registered directly, so I registered two sets of point cloud datasets from different angles. The obtained results are as follows: t = 0.063s t = 0.05s 

 In ICP coarse registration, when given different data sets (point clouds with different R and T), ICP may fall into the local optimal solution, so ICP is generally used in fine registration, and good initial values need to be provided. 

 In summary, in the crude registration scheme, the time-consuming order of the algorithm is NDT < FPFH < PFH < 3Dsc; where the FPFH feature is the improvement of the PFH feature descriptor. NDT takes less time, but from the observation in the above figure, the initial value is not accurate enough. The rotation matrix R and translation matrix T are listed. 

 ![avatar]( 20190305164857512.png) 

 ![avatar]( 20190305164915739.png) 

 ![avatar]( 20190305164931643.png) 

 ![avatar]( 20190305164954129.png) 

 2.4 Complete registration comparison, the following several crude registration schemes, plus fine registration. Then compare the results. 2.4.1 the result diagram analysis pfh + icp fpfh + icp 3Dsc + icp ndt + icp 

 ![avatar]( 20190305165047499.png) 

 ![avatar]( 20190305165111748.png) 

 2.4.2 time analysis 2.4.3 transformation matrix analysis  

 ![avatar]( 20190305165139347.png) 

 2.4.4 error analysis, it can be concluded that the highest registration accuracy is 3Dsc, but it takes the longest. Time: ndt < fpfh < pfh < 3dsc 

 Code download link https://download.csdn.net/download/weixin_43236944/10997992 https://download.csdn.net/download/weixin_43236944/10998014 

 After the update in the next two months, PCL-based QT development will be completed 



--------------------------------------------------------------------------------

The method of point cloud registration 

 Local feature-based registration: PFH, FPFH, 3Dsc 

 Registration based on global features: 4pcs, super4pcs, kfpcs 

 Probability-based registration: NDT 

 Realize the four-point method registration today 

 The principle of four-point registration: According to the affine invariance of the non-coplanar four points in the original point cloud, the transformation matrix is obtained from the target point cloud. 

 The code implementation is as follows: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573757377
  ```  
 The results are as follows: 

 ![avatar]( 2019041414563079.png) 

 ![avatar]( 20190414145648130.png) 

 After performing ICP precision registration on the above results 

 The results are as follows: 

 ![avatar]( 20190414151435104.png) 

 ![avatar]( 20190414151503247.png) 

 It can be seen that the transformed point cloud is more suitable for the target point cloud, and the transformation matrix is more accurate. 

 The same is true for other global registration methods, such as KFPCS registration. 

 The complete registration code will be uploaded later. 



--------------------------------------------------------------------------------

The goal of point cloud registration is to obtain the transformation matrix, namely the rotation matrix R and the translation matrix T, through registration according to the original point cloud and the target point cloud, and calculate the error to compare the matching results. There are mainly the following comparisons, based on local feature descriptors (PFH, FPFH, 3Dsc, Shot, etc.); icp registration; based on probability distribution (NDT); general steps of registration: extraction of key points, feature description, consistency estimation (the above can be summarized as coarse registration) Fine registration, error analysis, note: In registration, due to the characteristics of different point cloud datasets, different key points need to be extracted. 

 ![avatar]( 20200524220650616.JPG) 

 Demo display  

 ![avatar]( 20200524220711425.JPG) 

 Aggregate ICP resources 

 1，FilterReg: Robust and Efficient Probabilistic Point-Set Registration using Gaussian Filter and Twist pdf:Parameterization pdf:https://arxiv.org/pdf/1811.10136.pdf 

 2，Robust Point Cloud Registration Using Iterative Probabilistic Data Associations (“Robust ICP”) code: https://github.com/ethz-asl/robust_point_cloud_reg 

 3，Efficient Global Point-cloud registration code:https://github.com/nmellado/Super4PCS 

 4，Scale Ratio ICP for 3D Point Clouds with Different Scales 

 code:https://github.com/linbaowei/ScaleRatioICP 

 5，improved ICP for partial overlapping area situation code: https://github.com/jieliu/point_cloud_registration 

 6. SLAM algorithm for point cloud registration and splicing using ICP 

 code：https://github.com/kzampog/kabamaru 

 7,Fast Point Feature Histograms (FPFH) for 3D Registration. 

 PCL point cloud registration (1) 

 PCL point cloud registration (2) 

 8,3D Point Cloud Registration for Localization using a Deep Neural Network Auto-Encoder. 

 code：https://github.com/gilbaz/LORAX 

 9，Density Adaptive Point Set Registration. 

 code：https://github.com/felja633/DARE 

 10，Fast rotation search with stereographic projections for 3D registration 

 code：https://cs.adelaide.edu.au/~aparra/project/pcr/ 

 11，Discriminative Optimization: Theory and Applications to Point Cloud Registration pdf:https://www.researchgate.net/publication/320964941_Discriminative_Optimization_Theory_and_Applications_to_Point_Cloud_Registration 

 12，Markerless point cloud registration with keypoint-based 4-points congruent sets 

 pdf: https://www.isprs-ann-photogramm-remote-sens-spatial-inf-sci.net/II-5-W2/283/2013 / 

 13,Comparing ICP Variants on Real-World Data Sets code:https://github.com/ethz-asl/libpointmatcher 

 …… 

 Everyone is welcome to leave a message to supplement and summarize all registration algorithms. And you can join the free knowledge planet to exchange registration-related knowledge. Active people can join the WeChat sharing exchange group. 

 ![avatar]( 20200524220735488.JPG) 



--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

The following chapters 1, how to learn PCL and some basic knowledge 2, introduction to the IO port and common module in PCL 3, introduction to two data structures commonly used in PCL, KDtree and Octree, preface, three-dimensional point cloud segmentation is to divide point cloud objects with the same attributes, so as to process the point cloud objects separately, but because point cloud data is a highly redundant and uneven data structure, point cloud segmentation is challenging. 

 Since its launch in 2011, the Point Cloud Library (PCL) has been widely used in the industry. The library contains the most advanced 3D perception algorithms and includes the interface of LIDAR and 3D scanners, which makes the Point Cloud Library PCL continue to grow in the field of robotics. It has been updated to 1.9.1 version so far. In image segmentation, foreground and background segmentation processing is often used. In point cloud processing, for a given point cloud data, the goal of segmentation is to cluster points with similar characteristics into uniform areas. According to the segmentation results, it is applied to various aspects of scene analysis. The general method is to construct graphics according to the grid of the input point cloud, and use the normal of the boundary line, smoothness or concavo-convex information for clustering segmentation. In the article [1], the segmentation methods are investigated: concavo-convex segmentation, watershed analysis, hierarchical clustering, regional growth and spectral clustering. These methods are not only applied to images, but also widely used in the segmentation of point cloud data. 

 In computer vision, the segmentation of 2D images is a very classic problem, and has a history of more than ten years of research. Among them, traditional methods are more popular: Graph Cuts [2], including Normalized Cuts and Min Cuts. These methods are also suitable for 3D point cloud segmentation, and this part of the content has been open-sourced in PCL. 

 The point cloud segmentation algorithm should have the following three important properties: (1) For example, trees have different characteristics from cars. When the number of features in the point cloud data increases, the segmentation algorithm should be robust and able to learn how to automatically distinguish them. (2) Secondly, the segmentation should be able to infer the properties of these points in the sparse point cloud or determine which label belongs to them based on their adjacent information. (3) The segmentation algorithm should be able to apply to different scanners, even if the same scene generates point clouds in different scanners with different properties, and the quality and sparsity of the generated point clouds are also different. 

 The challenge of point cloud segmentation: Although point cloud data can determine the shape, size and some other properties of 3D objects, 3D point cloud data is usually noisy, sparse and disordered due to the limitations of sensors, such as the linear and angular rate changes of lidar, and the acquisition density of points is also uneven. In addition, the surface shape of point cloud data can be arbitrary, and there is no statistical distribution of data. So this brings a series of problems to the segmentation of point clouds. 

 ![avatar]( 20190522223410731.PNG) 

 数据集介绍：  Example scenes of (a) Cornell RGBD dataset, (b) VMR-Oakland dataset, © KITTI dataset, and (d) Robotic 3D Scan Repository 

 As shown in Figure 1, these data can be divided into two categories: indoor datasets captured by Kinect, and outdoor datasets captured by laser scanners (such as lidar). Applying segmentation algorithms to these public datasets allows researchers to better understand the advantages and disadvantages of segmentation algorithms 

 (1) Cornell RGBD dataset: This dataset has an indoor field of 52 labeled point clouds with RGB values (24 labeled office scenes and 28 labeled home scenes). Point cloud data is created from raw RGB-D images using RGBDSLAM [45]. The dataset consists of approximately 550 views with 2495 labels corresponding to 27 kinds of objects. (2) VMR-Oakland dataset: This dataset is a labeled point cloud data collected from the CMU campus via a mobile platform. The point clouds are collected using a laser scanner and saved in text format, with three real-valued coordinates written in each row. And training datasets, and test sets are provided. ** (3) KITTI dataset: ** This dataset includes a large amount of unorganized point cloud data captured by a 360 ° Velodyne laser scanner. It is the one with manually labeled true value boxes, such as the true value bounding box for outdoors such as cars, pedestrians, trams, trucks, and bicycles, for training dataset. (4) Robotic 3D Scan Repository: This dataset provides a collection of 3D point cloud datasets for indoor and outdoor environments. Some datasets include heat and color information. This is a huge collection of 3D point cloud data that can be used not only for segmentation but also for different other algorithms. However, these datasets have not been labeled and it may be that a pre-processing step is required before they can be used as input to segmentation algorithms. 

 ![avatar]( 20190522223538245.PNG) 

 Segmentation algorithm: Next, five traditional segmentation algorithms will be introduced: edge-based method, area-based method, attribute-based method, model-based method and graph-based optimization method (1) Edge-based method, edge is the basic feature of describing the shape of the point cloud object, this method detects the boundary of some areas of the point cloud to obtain the segmentation area, the principle of these methods is to locate the intensity change of the edge point, the paper [2] proposes an edge detection technology, by computing layer, detecting the change in the direction of the unit normal vector on the surface to fit the line segment. The paper [3] is based on the grouping of scan lines for fast segmentation. Although the segmentation speed of the edge-based method is relatively fast, the accuracy cannot be guaranteed, because the edge is very sensitive to noise and uneven or sparse point clouds. (2) Region-based segmentation methods, region-based methods use neighborhood information to classify nearby points with similar properties to obtain segmented regions and distinguish differences between different regions. Region-based methods are more accurate than edge-based methods. But they have problems with over-segmentation or under-segmentation and how to accurately determine the boundary of the region. Researchers divide region-based methods into two categories: seeded region (or bottom-up) methods and non-seeded region (or top-down) methods. 

 Seed area method: Seed-based area segmentation starts by selecting multiple seed points. From these seed points as the starting point, the point cloud area is gradually formed by adding the neighborhood points of the seed. The original algorithm was proposed in the paper [4]. The algorithm mainly consists of two steps: (1) identify the seed points based on the curvature of each point, and (2) grow the seed points according to a predetermined standard, which can be the similarity of the points and the similarity of the surface of the point cloud. This method is also very sensitive to noise points and is time-consuming. But there have been many subsequent improvements based on this method. For example, for the method of regional growth of lidar data, it is proposed to grow seed points based on the normal vector of seed points and the distance from the growth plane. The seed area method is highly dependent on the selected seed points. Inaccurate selection of seed points can affect the segmentation process and may lead to under-segmentation or over-segmentation. Selecting seed points as well as controlling the growth process is time-consuming. The segmentation result may be sensitive to the selected compatibility threshold. Another difficulty is deciding whether to add points in a given area because this method is also sensitive to noise from point clouds. 

 Non-seeded region method: This method is based on a top-down approach. First, all points are divided into a region. Then the subdivision process begins to divide it into smaller regions. Paper [5] uses this method to guide the process of clustering planar regions to reconstruct the complete geometry of the building. This work introduces a segmentation method based on the confidence rate of local regions as planes. The limitation of this method is that it will also be possible to over-segment, and it does not perform well when dividing other objects (e.g. trees). The main difficulty of non-seeded region methods is deciding where and how to segment. Another limitation of these methods is that they require a lot of prior knowledge (e.g., object model, number of regions, etc.), and then this unknown prior knowledge is usually unknown in complex scenarios. 

 (3) Attribute-based method, which is a robust segmentation method based on the properties of point cloud data, this method generally includes two separate steps (1) The first step, attribute-based calculation, in the second step, will be clustered according to the properties of the calculated points. This clustering method can generally adapt to the spatial relationship and various properties of the point cloud. Finally, point clouds with different properties are segmented, but the limitation of this method is that they are highly dependent on the quality of derived properties, so the first step is required to accurately calculate the properties of the point cloud data, so that the best effect can be segmented according to the category of properties in the second step. The paper [6] is realized by this method, and proposes a clustering analysis method based on the feature space. In this method, a normal vector is derived using an adaptive slope neighborhood system. The properties of the point cloud data, such as distance, point density, and the distribution of points in the horizontal or vertical directions, are used to define the domain between the measurement points. Then the difference between the slope of the normal vector in each direction and the data of the point neighborhood is used as the property of the clustering. This method can eliminate the influence of outliers and noise. The property-based method is an efficient way to segment the point cloud into the same attribute area, and the segmentation results are flexible and accurate. However, these methods rely on the definition of the neighborhood between points and the point density of the point cloud data. Another limitation of this approach is that it is time-consuming when dealing with multidimensional properties of a large number of input points. 

 (4) Model-based method, which groups point clouds based on geometric shapes such as spheres, cones, planes, and cylinders. According to these shapes, points with the same mathematical representation will be divided into the same set of points. A well-known algorithm, RANSAC (RANdom SAmple Consensus), is introduced in the paper [7]. RANSAC is a powerful model for detecting mathematical features such as lines and circles. This application is extremely extensive and can be considered the most advanced technology for model fitting. The methods that need to be improved in the segmentation of 3D point clouds are inherited from this method. The model-based method has pure mathematical principles, is fast and powerful, and has unique value. The main limitation of this method is the inaccuracy of dealing with different point clouds. This method has been implemented in point cloud libraries based on various models such as line, plane, circle, etc. 

 (5) Graph-based optimization methods. Graph-based optimization methods are very popular in the application of robots. The well-known method is the FH algorithm [7]. This method is simple and efficient, and like the Kruskal algorithm, it is used to find the minimum spanning tree in the graph. Much of the work of graph-based methods is put into probabilistic inference models, such as conditional random fields (CRFs), methods that use CRFs to label points with different geometric surface primitives. Graph-based optimization methods successfully segment point clouds in complex urban environments, with near real-time performance. For comparison with other methods, graph-based methods can perform complex scenes in point cloud data. However, these methods are usually not able to run in real time. Some of them may require steps such as offline training. 

 In summary, the segmentation methods are divided into five categories above. However, in general, there are two basic methods. The first method uses pure mathematical models and geometric inference techniques, such as region growth or model fitting, to fit linear and nonlinear models to point cloud data. This method allows fast run times to achieve good results. The limitations of this method are that it is difficult to choose the size of the model when fitting objects, is sensitive to noise and does not work well in complex scenes. 

 The second method uses the method of feature descriptors to extract 3D features from point cloud data, and uses machine learning techniques to learn different classes of object types, and then uses the resulting model to classify the acquired data. In complex scenarios, machine learning techniques will outperform techniques based purely on geometric reasoning. The reason is that it is difficult to find and fit complex geometric figures to objects due to noise, uneven density, and occlusion in point cloud data. Although machine learning techniques can provide better results, they are usually slow and depend on the results of the feature extraction process. These algorithms have been implemented in PCL and all have ready-made demos to view the effect. 

 The following will introduce the segmentation module in PCL point cloud in detail. This module is based on the above basic modules, such as how to construct point cloud data into kdtree or Octree structure and use FLANN (nearest neighbor search) to find the relationship between points and surrounding views. Classes commonly used in PCL are as follows: class pcl :: ConditionalEuclideanClustering < PointT > This class implements the classification algorithm of European clustering for setting conditions 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573742942
  ```  
 //The above is a field based on point cloud intensity information for setting, that is, the intensity information requirement of two points/ 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573742942
  ```  
 //Add our conditional function here 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573742942
  ```  
 Class pcl :: CPC Segmentation < PointT > A segmentation algorithm for segmenting hyperprime graphs. It uses local concavity-induced plane cutting for recursive segmentation. Use locally constrained directed RANSAC for segmentation. 

 CPC segmentation and LCCP segmentation are inherited relationships: specific papers can be viewed in the literature 

>  M. Schoeler, J. Papon, F. Woergoetter Constrained Planar Cuts - Object Partitioning for Point Clouds In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR) 2015 

 Class pcl :: EuclideanClusterExtraction < PointT > Euclidean clustering extraction is a point cloud class for clustering and segmentation in the Euclidean sense. This function is often used. It has been mentioned many times in the previous examples, so I will not give an example here. You can check the relevant blog content 

 Class pcl :: LabeledEuclideanClusterExtraction < PointT > labeledeuclidenclusterextraction represents a segmented class for clustering extraction with label information in the Euclidean sense, 

 Class pcl :: ExtractPolygonalPrismData < PointT > ExtractPolygonalPrismData Use a set of point indices that represent a plane model and together with the given height generate a 3D polygonal prism. Then use the polygonal prism to split all the points that lie within it. One example of its use is to extract data that lies within a set of 3D boundaries (e.g. objects supported by planes). 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573742942
  ```  
 Class pcl :: GrabCut < PointT > implements GrabCut splitting. 

 class pcl::segmentation::detail::RandomWalker< Graph, EdgeWeightMap, VertexColorMap > 

 Multi-Label Graph Segmentation for Random Walking 

>  Random Walks for Image Segmentation 

 Class pcl :: LC CP Segmentation < PointT > A simple segmentation algorithm that divides a hyperprime graph into locally convex connected hyperprime groups separated by concave boundaries. Related papers 

>  S. C. Stein, M. Schoeler, J. Papon, F. Woergoetter Object Partitioning using Local Convexity In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR) 2014 

 Class pcl :: SACSegmentationFromNormals < PointT, PointNT > Binding Point Cloud Data Surface Normal Vector Segmentation Using RANSAC Method 

 Class pcl :: SeededHueSegmentation class pcl :: SegmentDifferences < PointT > SegmentDifferences takes the difference between two spatially aligned point clouds and returns the difference between them at the maximum given distance threshold. 

 Class pcl :: SupervoxelClustering < PointT > implements a super voxel algorithm based on voxel structure, normals and RGB values. The specific paper is as follows Voxel Cloud Connectivity Segmentation - Supervoxels from PointClouds In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR) 2013 

 The next chapter will specifically introduce the model-based segmentation method implemented in PCL 

>  【1】A. Shamir, Segmentation and shape extraction of 3D boundary meshes (state of the art report), in Eurographics, 2006 【2】 B. Bhanu, S. Lee,C. Ho, and T. Henderson, Range data processing:Representation of surfaces by edges. In proc.int. Pattern recognition conf, 1896 【3】X.Y. Jiang, H. Bunke, and U. Meier, Fast range image segmentation using high level segmentation primitives, In 3rd IEEE Workshop on Applications of Compute Vision, USA, 1996 【4】P.J. Besl, R.C. Jain, Segmentation through variable order surface fitting, IEEE Transaction on Pattern Analysis and Machine Intelligence 10, 1988. 【5】J. Chen, B.Chen, Architectural modeling from sparsely scanned range data. Int. J. Comput. Vision 78, 2008. 【6】S. Filin, N. Pfeifer, Segmentation of airborne data using a slope adaptive filter, ISPRS J. Photogramm. Remote Sens., vol. 60, pp. 71- 80, 2006. 【7】M. Fischler, R. Bolles, Random sample consensus: a paradigm for model fitting with applications to image analysis and automated cartography Communications of the ACM 【8】P.F. Felzenszwalb, D.P. Huttenlocher, Efficient Graph-Based Image Segmentation, International Journal of Computer Vision, 59(2), 2004. 

 ![avatar]( 20190522224320789.PNG) 



--------------------------------------------------------------------------------

 ![avatar]( d6a79990831b4925a8a805e2b6269730.png) 

 论文地址:Semantic Segmentation for Real Point Cloud Scenes via Bilateral Augmentation and Adaptive Fusion 

##  Contribution to this paper 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573755032
  ```  
##  II. Bilateral Context Module 

 The Bilateral Context component consists of multiple Bilateral Context Blocks. Let's first look at the internal structure of a BCB, which consists of Bilateral Augmentation and Mixed Local Aggregation, as shown below: 

 ![avatar]( 8d39f09c11eb4138991b8604416034a5.png) 

###  2.1. Bilateral polymerization 

 For a central point, it represents the geometric position information (x, y, z) of the point, and represents other feature information (color, intensity, etc.) of the point. Use KNN to search for k domain points around the point. Combine the absolute features of the point and the relative features of the domain point as local semantic context information. The specific implementation is to copy the features of the point several times, and then subtract the eigenvalues of the points from the eigenvalues of the points around the points to get the relative eigenvalues, and splice the relative eigenvalues and the eigenvalues of the points in the feature dimension. (In the source code interpretation, I will explain the specific operation according to the code.) Do a similar operation on the coordinates of a point, combining the absolute coordinates of the point with the relative coordinates of the surrounding neighborhood points as local geometric context information.  

 The above operation can aggregate the neighborhood information around a point to that point, and obtain local context information in geometric space and feature space. But the newly obtained local context information is not enough to express the domain information. There are the following two problems. (1) Strict encoding under fixed constraints in 3D space may weaken the generalization ability of G0019 in high-dimensional feature space, and (2) there may be redundancy in the representation of the closed region of G0019 neighborhood. Note: (1) (2) The problem about the existence of local context information comes from Google Translate. I myself have not figured out how to express it in a simple and clear way. I will put it aside for the time being. Readers are cautious. 

 The author designs to enhance the geometric information of neighborhood points through rich local semantic context information, mainly to adjust the neighborhood geometric information by learning an offset value through MLP. The specific methods are as follows: First, the generated local semantic context information is input into an MLP to generate a neighborhood offset value, and then the offset value is added to the geometric information of the domain point to obtain. 

  As the enhanced neighborhood point geometric information and the local geometric context information are spliced together, the enhanced local geometric context information is obtained, namely: here, the local geometric context information is adjusted through the local semantic context information. Similarly, the enhanced local geometric context information is used to enhance the neighborhood feature information. The same is to use MLP to obtain the offset value, and then add the offset value and the characteristic value of the neighborhood to obtain the enhanced neighborhood feature information. The calculation formula is as follows: 

 The feature information of the enhanced neighborhood points is combined with the local semantic context information to obtain the enhanced local semantic context information. Here, the local semantic context information is adjusted by the enhanced local geometric context information. 

 Finally, MLP is used to further process the enhanced local geometric context information and local semantic context information and stack them together to obtain the enhanced local context information.  

###  2.2. Enhanced losses 

 In order to maintain the integrity of geometric shapes when enhancing geometric information, the L2 loss is used to limit the enhancement.  

###  2.3. Mixed local polymerization 

 Note that the calculations we mentioned before are all about a point, and the local context information of the point is calculated through the neighborhood points of this point. At this time, all K domain points have a set of features. We need to aggregate the features of the K neighborhood points. The general operation is to use a non-parametric symmetric function (such as max). Although the non-parametric symmetric function can effectively aggregate the local information of points, this operation cannot effectively represent local differences, especially close points often contain similar local context information. Therefore, the author proposes a method of hybrid local aggregation. 

 The first is the maximum pooling method, which maximizes the K values of each feature as the value of the feature at the point. i.e.: 

 The second is to learn the mean point of the local neighborhood of the point through MLP, and use the feature of the point as the feature of the point, that is. 

 Finally, the above two aggregation features are spliced together to get the final feature of point i.  

###  2.4. Bilateral context components 

 The bilateral context component is to combine the bilateral context modules, and continuously output the downsampled point into the BCB, which is also the corresponding encoder part. 

 ![avatar]( e3f51f3851e24781bcd2a16f0ab2f318.png) 

##  三、Adaptive Fusion Module 

 ![avatar]( 1a93af7bd43344199cfdf7e6949180ff.png) 

 This part corresponds to the decoder, which is also easier to understand. The encoder will output feature maps of different resolutions, which are defined as step-by-step upsampling of the output of each layer to obtain a full-size feature map. Note that each upsampling requires fusing the feature maps of the previous layer. 

 Then the full-size feature maps sampled on multiple scales need to be fused. In order to obtain important information of different sizes, the author first inputs the full-size feature maps into the MLP to obtain point-level information, and then uses sofmax to normalize the point-level information. 

 Finally, by fusing the normalized point-level information and the upsampled full-size feature map, a comprehensive feature map Sout for semantic segmentation is obtained. 

##  IV. Network structure 

 This part will be explained in detail in the source code reading. 

##  V. Model training 

 BAAF-Net training Semantic3D dataset BAAF-Net training S3DIS dataset 



--------------------------------------------------------------------------------

##  I. PointNet 

###  1.1. Interpretation of the paper 

 Paper reading: pointnet 

###  1.2. Open dataset testing 

 Point Cloud Semantic Segmentation: PointNet Training S3DIS Dataset 

###  1.3. Source code interpretation 

 Pointnet source code reading: data preprocessing pointnet source code reading: training pointnet source code reading: model pointnet source code reading: test 

##  PointNet ++ 

###  2.1. Interpretation of the paper 

 Paper reading: PointNet ++ 

###  2.2. Open dataset testing 

 Point cloud semantic segmentation: pointnet ++ training S3DIS dataset 

###  2.3. Source code interpretation 

 Point cloud sampling FPS principle and implementation, source code reading: PointNet ++ 

##  III. KPConv 

###  3.1. Interpretation of the paper 

 Point Cloud Semantic Segmentation: KPConv Interpretation - Updating 

###  3.2. Open dataset testing 

 S3DIS Test: Point Cloud Semantic Segmentation: KPConv Training S3DIS dataset Semantic3D Test: Training Semantic3D dataset with KPConv in tensorflow2.0 environment 

###  3.3. Source code interpretation 

 Source code reading: KPConv's Dataset class, source code reading: KPConv's Dataset class visual test 

###  3.4. Training your own dataset 

##  、RandLA-Net 

###  4.1. Interpretation of the paper 

 Paper Address: RandLA-Net: Efficient Semantic Segmentation of Large-Scale Point Clouds: RandLA-Net Interpretation 

###  4.2. Open dataset testing 

 Project Address: RandLA-Net S3DIS Test: Train the S3DIS dataset using RandLA-Net in the tensorflow 2.0 environment. Semantic3D Test: Train the Semantic3D dataset using RandLA-Net in the tensorflow 2.0 environment. Train the RandLA-Net point cloud semantic segmentation model under Win10 system. 

###  4.3. Source code interpretation 

 Tf1.x RandLA-Net source code interpretation (1): Data preprocessing 

 Tf1.x RandLA-Net source code interpretation (2): Dataset 

 Tf1.x RandLA-Net Source Code Interpretation (3): Network Architecture 

 Tf1.x RandLA-Net source code interpretation (4): Model training 

 Tf1.x RandLA-Net Source Code Interpretation (5): Testing 

###  4.4. Training your own dataset 

 Point Cloud Semantic Segmentation: Training Your Own Dataset with RandLA-Net 

###  4.5 Deployment 

 Python Deployment: Point Cloud Semantic Segmentation: RandLANet Model Inference Deployment C++ Deployment: Point Cloud Semantic Segmentation: RandLANet Model Inference C++ Deployment 

## 

###  5.1. Interpretation of the paper 

 Point cloud semantic segmentation: BAAF-Net interpretation 

###  5.2. Open dataset testing 

 S3DIS training: BAAF-Net training S3DIS dataset Semantic3D training: BAAF-Net training Semantic3D dataset 

###  5.3. Source code interpretation 

 BAAF-Net source code reading 

###  5.4. Training your own dataset 



--------------------------------------------------------------------------------

#  I. Preparation 

##  1.1, deep learning knowledge 

 MLP, convolution can be 

##  1.2. Point cloud operation 

 The basic structure of point cloud data is coordinates + attribute characteristics, and there are various storage formats. We need to know how to parse point cloud data in different storage formats, that is, how to read and write point cloud data. Refer to different formats point cloud storage structure (txt, pcd, las, ply) sorting and basic reading and writing, visualization methods. The basic transformation of point cloud Refer to 3D point cloud transformation (translation, rotation, scaling) and python to realize 3D point cloud transformation (translation, rotation, scaling) C++ 

#  Open dataset testing 

 Understanding public datasets such as Semantic3D, S3DIS, KITTI, etc., I used RandLANet to test Semantic3D and S3DIS myself. Due to the large dataset of KITTI, I did not do this test. I will make up for it later when I have the opportunity. 

##  3.1、Semantic3D 

 The reference article in Ubuntu environment uses RandLA-Net to train Semantic 3D dataset in tensorflow 2.0 environment. Training RandLA-Net point cloud semantic segmentation model under Windwos environment Win10 system. 

##  3.2、S3DIS 

 Ubuntu environment Reference article Training S3DIS dataset using RandLA-Net in tensorflow 2.0 environment. 

 Project Address: RandLA-Net 

#  III. Paper reading 

 We can start reading the paper when training the public dataset. Paper address: RandLA-Net: Efficient Semantic Segmentation of Large-Scale Point Clouds. My own understanding of point cloud semantic segmentation: RandLA-Net interpretation. 

#  IV. Source code interpretation 

 Reading the source code is to better tune parameters on your dataset. Interpretation of RandLA-Net source code of tf1.x version (1): Data preprocessing 

 Tf1.x RandLA-Net source code interpretation (2): Dataset 

 Tf1.x RandLA-Net Source Code Interpretation (3): Network Architecture 

 Tf1.x RandLA-Net source code interpretation (4): Model training 

 Tf1.x RandLA-Net Source Code Interpretation (5): Testing 

#  V. Train your own dataset 

 Point Cloud Semantic Segmentation: Training Your Own Dataset with RandLA-Net 

#  Deployment of python production environment 

 Point cloud semantic segmentation: RandLANet model inference deployment 

#  Deployment C++ production environment 

 Point Cloud Semantic Segmentation: RandLANet Model Inference C++ Deployment (1) Point Cloud Semantic Segmentation: RandLANet Model Inference C++ Deployment (2) 



--------------------------------------------------------------------------------

 The difficulties of point cloud convolution compared to ordinary image convolution: points are sparse points in space, disorder, rotation invariance 

#  Point convolution 

 The general formula of point convolution is given in the paper, but it is a bit difficult to understand the point cloud convolution process directly from the formula. Therefore, we will explain the process of point convolution through images first, and then look back at the formula. 

 ![avatar]( bd7ac6adc1ed45f6b1806a2be7176f25.png) 

 The above figure is the graphic process of image convolution (left) and point convolution (right) given by the author in the paper. Personally, I think the key to understanding the above figure is the expression form. We can see that the author is based on pixels or points to show the process of convolution, but in this way, the weight of the convolution kernel also needs to be organized according to the position of pixels and points, which is different from our general understanding of the convolution process. Therefore, I will review the process of image convolution in a channel-based manner first. 

##  1.1. Channel-based image convolution 

 ![avatar]( 22e7e272e2f14b7b948f06be3b6bec35.png) 

 The above figure shows the process of multi-channel convolution more intuitively. The input data size is (3, 6, 6), indicating three channels, each with a height of 6 and a width of 6. Then, taking one of the points as an example, the process of 3x3 convolution is shown. The size of the convolution kernel is (4, 3, 3), indicating that there are four convolution kernels (represented by different colors), so the output channel is 4, and the width, height and input are consistent. 

 The key point is to look at the 3x3 convolution process of a point. First, take out the 3x3 data around this point. For one of the convolution kernels, the input data and the channel of the convolution kernels are multiplied by the corresponding points, and then added to obtain a characteristic value after convolution. Four convolution kernels will obtain four characteristic values, and then swipe in turn to complete the entire operation. 

 The convolution process introduced above is based on the channel, which is more intuitive. Let's try to illustrate the image convolution process given in the KPConv author's paper by way of diagrams. 

##  1.2. Pixel-based image convolution 

 At the beginning, I introduced that the graphic process given by the author's paper is based on pixels. The following figure shows the calculation process on a pixel. 

 ![avatar]( 54c3dcf41e3b4872a83300e93c0767f0.png) 

 In the figure above, pij represents the grey release value of the j-th channel of the i-th pixel, such as p23 represents the value of the third channel on the second pixel, wij represents the weight value of the j-th channel at the i-th position of a convolution kernel, and w23 represents the weight value of the third channel at the second position of the convolution kernel, which corresponds to p23. Different convolution kernels are represented by different colors in the figure. 

 First, we take out all the channel data at the first pixel position and put them together, then take out the weights at the positions corresponding to the first pixel of all convolutional kernels and splice them together (as shown in the figure above), and then do matrix multiplication to obtain 4 new feature values at the first pixel position. 

 Then do the same for other pixels, as shown below (the middle pixel is omitted): 

 ![avatar]( aeb3de20a60b42ada00069d4e4d6e45f.png) 

 After the convolution operation on each point is completed, all the pixels on each output feature channel are summed, so that the eigenvalues of the center point after convolution are obtained. If you compare them with channels, you will find that the results are the same. 

 Here we should understand the expression form in the author's paper. The size is [K, Din, Dout], which is based on pixels. K represents the K pixel positions of the convolution kernel corresponding to the input data, Din corresponds to the Din input features of each pixel, and Dout corresponds to the Dout output features of each pixel. 

##  1.3. Point cloud convolution 

 Let's take a look at how to generalize image convolution operations to point clouds. 

 ![avatar]( 929ed0bceba84919aaa4b8a7eb56298c.png) 

 The author of the paper likens the pixel-based image convolution process to the point-based convolution operation of the cloud. We take the above figure as an example, the input data is 4 points (the number of features per point is 4), the number of points in the convolution kernel is 7 (the number of features per kernel is 4), and the number of features in the output point is 5, so there are 5 convolution kernels. 

 ![avatar]( 79d560bd950e4b4abb576705fc97670f.png) 

 The above figure represents the weights of 5 convolution kernels, because the output feature channel is 5. For one of the convolution kernels wij represents the weight value on the jth channel at the i-th position. 

 In Section 1.2, we introduced how to reorganize the weights in the convolution kernel. Similarly, the point convolution process is based on points, organizing all the weights on each point together. As shown below: 

 ![avatar]( bac6fa64d82743a48b9a44d0fa059c19.png) 

 At this time, there is a problem that the characteristics of the points in the point cloud cannot correspond to the weights in the convolution kernel one-to-one. The problem here is not caused by the inconsistency between the number of points and the number of points in the convolution kernel. Even if the number is the same, the two cannot correspond one-to-one, because the positions of the points in the point cloud are not fixed. Therefore, a core of the point convolution process is how to establish the positional relationship between the input points and the points in the convolution kernel. 

 KPConv redistributes the weights in the convolution kernel to each point in proportion by establishing a correlation between the points in the point cloud and the points in the convolution kernel. 

 ![avatar]( aae84b4c6b094ab9b60769d615189f18.png) 

 The above figure shows how to establish the relationship between the input point and the point in the convolutional kernel, mainly through the Euclidean distance. The closer the two points are, the greater the correlation. Take the first point of the input as an example, calculate the distance between the point and the point in the convolutional kernel, and then calculate according to the formula, indicating the correlation between the first point in the input point cloud and the first point in the convolutional kernel. 

 Then let's take a look at the formula expression for this step: 

 ![avatar]( 4f0f44ff90c1459c9a3232556115cfde.png) 

 It represents the Euclidean distance between the points in the point cloud and the points in the convolution kernel. Please note that the sum in the formula is different from the point coordinates in the graph. The coordinates in the formula represent the coordinates of a certain point, which represent the coordinates after decentralization. It is the influence distance of Kernel Points, which will be selected according to the input density. 

 ![avatar]( 74e51dbfec4a4da2807cc151488bfb14.png) 

 After calculating the correlation between each input point and the points in the convolution kernel, the weights of each point in the convolution kernel are reassigned. As shown in the figure above, the first point is taken as an example. The weights and correlation coefficients are multiplied in sequence, and then summed to obtain the weights corresponding to the first point. The corresponding weights are calculated at points 2, 3, and 4 according to the same operation. 

 Let's take a look at the formula for this step: 

 ![avatar]( 93682589c7074a0595f6b0172d11b411.png) 

 The above formula expresses the new convolution kernel corresponding to the i-th input point, which refers to all the weights on the first point in the original convolution kernel, and represents the correlation between the first input point and the first point in the convolution kernel. 

 ![avatar]( e9718d110249490186d65deee65434d9.png) 

 The remaining operations are the same as image convolution. The features of the points are multiplied by the corresponding weights in a matrix, and then summed in the feature dimensions to obtain the features after the center point is convoluted. 

 Corresponds to the first formula: 

 ![avatar]( 73025c4f85624136bc1c8a47931bb602.png) 

 The local neighborhood of a point can be regarded as a spherical neighborhood drawn by a central point with a radius, i.e. 

#  Second, regular and deformable convolutions 

 In the first section, we tried to understand the process of point convolution graphically. We found that a key to point convolution is how to establish the correlation between the input points and the points in the convolution kernel. KPConv is based on the distance between the points to establish the correlation between each other. We know the position of the input points, but how to get the position coordinates of the points in the convolution kernel? This leads to the regular point cloud convolution kernel deformable point cloud convolution 

##  2.1. Regular point cloud convolution 

 ![avatar]( dd589dc35f824f0caed78a3808046766.png) 

##  2.2. Deformable point cloud convolution 

 ![avatar]( dfd9c54940c749a18a61496216c7bc49.png) 

#  Point convolutional layer 

##  3.1. Downsampling strategy 

##  3.2. Pooling layer 

##  3.3. KPConv layer 

##  3.4. Network hyperparameters 

#  IV. Semantic Segmentation Network 

 ![avatar]( 86f58b210cb4467c8e6eda8c5fc5b3b0.png) 

#  IV. Training dataset 

 See KPConv training S3DIS dataset, KPConv training Semantic3D dataset 



--------------------------------------------------------------------------------

The code uses the github project provided by the KPconv author. 

##  KPConv training S3DIS dataset 

 1. Data preparation, this part refers to RandLA-Net training S3DIS dataset 2. Compile C++ code, compile method refers to INSTALL.md, divided into linux and win10 systems. Find the cpp_wrappers folder under the Ubuntu system and execute it directly in the end point 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573775433
  ```  
 In the win10 system, compile cpp_neighbors and cpp_subsampling separately, execute 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573775433
  ```  
 and 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573775433
  ```  
 I myself in the win10 system under the test found that the execution of build.bat will prompt no py command, if you also encounter the same problem, you can follow the following operation to compile, compile cpp_neighbors, under cmd into the cpp_warppers\ cpp_neighbors folder, execute the following statement 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573775433
  ```  
 The method of compiling cpp_subsampling is the same as above. 

 3. To train the model, modify the data address before training, in line 88 of the datasets\ S3DIS.py script 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573775433
  ```  
 The S3DIS dataset has a total of 6 regions of data, namely Area_1, Area_2, Area_3, Area_4, Area_5, Area_6. The author uses Area_5 as the test set and the other 5 regions as the training dataset. See code datasets\ S3DIS.py line 114 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573775433
  ```  
 Then start training the model 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573775433
  ```  


--------------------------------------------------------------------------------

 Pointnet ++ Project Address: Pointnet_Pointnet2_pytorch 

#  First, data preprocessing 

 Download the original data source set and then perform the preprocessing operation, which is actually saving the point cloud in txt format to npy format. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573783562
  ```  
#  II. Training 

 The training code is train_semseg.py, you need to specify the model pointnet2_sem_seg, verify the data area5, log path pointnet2_sem_seg. The author's trained model has been given in github, and if you want to retrain it, you can replace it with a different log_dir. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573783562
  ```  
  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573783562
  ```  
 ![avatar]( 0a618b718c844b699b3fe4ca53cab985.png) 

#  III. Testing 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573783562
  ```  
#  4. 60% off cross-validation 



--------------------------------------------------------------------------------

 Project address: pointnet This time we use the pointnet network to do semantic segmentation. The code is in the sem_seg folder in the pointnet project, which also README.md introduces the training process. 

#  First, data preparation 

##  1.1. Data download 

 Download the original data source, S3DIS has data for 6 regions. 

 The processed h5 format data indoor3d_sem_hdf5_data.zip downloaded. This is the author's processed h5 format point cloud file. Pointnet directly uses this data for training. For each room, the data is cut according to a block of 1mx1m, and then 4096 points are selected as 1 line of data. When 1000 lines are enough, it is saved as a .h5 file. There are 24 h5 files in total. The first 23 files are 1000 lines, and the last h5 file has 585 lines. There are also two txt files, all_files .txt and room_filelist .txt. all_files .txt records the name of each h5 file. Each line in room_filelist .txt is the name of a room in an area, indicating which room the line data is taken from. 

#  II. Training 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573759548
  ```  
 ![avatar]( a0bbc0f8ef5a440aa4efa986a025feb0.png) 

 Training process  

#  III. Testing 

 First, the original data source is processed to generate a .npy file 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573759548
  ```  
  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573759548
  ```  
 When executing the above statement, the error unsupported operand type (s) for +: 'range' and'list 'may be reported, which corresponds to the sample_data function of indoor3d_util.py. Add a list before range (N). 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573759548
  ```  
 After execution, the real point cloud and test point cloud files corresponding to each room will be generated in the log6/dump folder. There are two formats of obj and txt. But during my testing, I found that the obj file cannot display the label of each point, the prediction file can display the color and label normally, and the txt corresponding to the real point cloud has only one label, which cannot be displayed in cloudcompare. Check the code and send the following modifications. In the eval_one_epoch () of the batch_inference.py file, the corresponding part of the txt file is saved, and the coordinates and colors of the points are added when the real point cloud is saved. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573759548
  ```  
 ![avatar]( baf52bbb3e1b4aa8be108e44119d2f69.png) 

 Rerun the test operation  

 ![avatar]( b9e865da5e0f4621960a1e8ed1ec6b51.png) 

 The opening effect in cloudcompare is as follows:  

#  4. 60% off cross-validation 

 The training and validation of S3DIS data is generally a 60-fold cross-validation method, that is, each time a region is selected as the test set, and the remaining 5 rooms are used as the training dataset to train a model, so that 6 models can be obtained, and then the test results of the 6 models are put together to calculate the accuracy uniformly. 

 ![avatar]( c21c2cfdfd5946d9a78396b2ada32400.png) 

 The author gives the training tutorial of using area_6 as the test set in readme. We need to train the remaining 5 regions as the test set in turn. Among them, when testing, we need to make a areai_data_label file. The author has given area6_data_label .txt, which records the npy file path of each room in area6. We need to regenerate the other 5 files, as shown in the figure below, the code is as follows 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573759548
  ```  
 When the 6 models are trained, the accuracy of 60% off verification can be calculated, and the executable code is eval_iou_accuracy.py 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573759548
  ```  
 ![avatar]( de42ab5cf55d42c8b3ccfff680e6444f.png) 

  It can be seen that the miou is 46.69 after 60% off cross-validation, compared to 47.71 in the author's paper. 



--------------------------------------------------------------------------------

#  Local feature aggregation module 

 ![avatar]( e4df5f6fc00e48dda4f11c54156ace06.png) 

##  1.1. Local Spatial Encoding 

 Function: Obtain the neighborhood characteristics of each point. Method: There are mainly 3 steps to obtain the local space code. Taking a point as an example, the first step is to find the neighborhood points (Finding Neighbouring Points), and find the K points (including the point) closest to the point through the KNN algorithm; at this time, the neighborhood expression of the point is a matrix of K X (3 + d). The second step is Relative Point Encoding, which is implemented through a shared MLP network in the form of:  

 The subscript in this formula refers to point A, which refers to the first point in the neighborhood of A, and this step is to re-encode the first point in the neighborhood of point A. Create a shared MLP network, the input of this network is the coordinates of the center point A, the coordinates of the first point, the coordinate difference between A and the first point, and the distance between A and the first point, so the input size is 3 + 3 + 3 + 1 = 10, and the characteristics and dimensions of the relative points encoded after MLP are (consistent with the attribute feature size of the point cloud). All K points in the neighborhood of A are encoded in relative positions. 

 The third step is point feature enhancement (Point Feature Augmentation). For the kth point in the neighborhood of point A, the recoded positional features and the original attribute features are stacked to obtain the enhanced feature vector, and finally an enhanced feature vector is obtained. 

##  1.2. Attentive Pooling 

 Function: Aggregate neighborhood features, method: attention score and weight summation, first step, calculate attention score (Compute Attention Scores): Take the local space encoded feature vector as input, input the {k} th feature vector into the MLP network, and then calculate the weight corresponding to the feature vector through softmax. 

 The second step is to sum the weights (Weighted Summation): Multiply the calculated weights by the enhanced eigenvectors, and then sum the K weighted eigenvectors to obtain a new eigenvector. 

 1.1 and 1.2 calculate the characteristics of a point. For each of the N points in the input, 1.1 and 1.2 are calculated once, so that each point aggregates information about the surrounding neighborhood points. 

##  1.3. Dilated Residual Block 

 Function: Increase the receptive field, speed up the learning speed, and improve the accuracy. Method: In order to expand the receptive field, perform two local space coding and attention pooling in an expanded residual block. At the same time, learn from the residual structure of resnet and other networks, and use short cut operations to add the input features and the enhanced features. 

#  Semantic Segmentation Network 

 ![avatar]( b356274ddaad42e48e4af581d2f30966.png) 

 The RandLA-Net semantic segmentation network uses an Encoder-Decoder structure similar to Unet, using the coordinates and attributes of points as input. 

 In the decoding stage, there are 4 coding layers, each coding layer has an LFA module and a random downsampling operation. The LFA module is used to improve the feature dimension of the point, and the random downsampling is used to reduce the number of points. Only 1/4 of the points in each coding layer are retained (), and the feature dimension of each point is constantly increasing (). 

 In the decoding stage, the nearest neighbor interpolation is used to realize the upsampling of the points. After the upsampling, the MLP network is used to reduce the feature dimension of the points. At the same time, the decoded features are stacked with the features corresponding to the encoding stage using the skip connection operation. 

 The last part is the semantic segmentation stage, where the semantic category of each point is predicted by three fully connected layers plus a dropout layer. 

#  III. Data preprocessing 

 Personally, I think the data preprocessing in point cloud semantic segmentation is a very important part. How to organize the input network point cloud sample set reasonably has a great impact on the final model accuracy. In this part, I plan to introduce in detail how to use the RandLA model to train the Semantic 3D dataset. 



--------------------------------------------------------------------------------

 The last blog entry in the RandLANet series. 

 After the model training is stable, it is generally sampled C++ to formally deploy the environment, that is, to use C++ for forward reasoning. One reason is that the use of python deployment requires additional environment installation, which is not convenient for transplantation. The second is that the efficiency is not as good as C++. 

 When deploying a model with C++ version of TensorFlow, you typically do the following three steps: 

#  First, ckpt model to pb model 

 The key point of the ckpt to pb model is to know the name of the output node. This step can directly go to the training code to find the sess.run () sentence. sess.run () receives the return that is the name of the output node we need to do the model conversion. Directly print these variables to get the name of the output node we need. However, the randlanet used in this article is somewhat special in the process of converting the ckpt model to the pb model. Please make sure you have fully understood the testing process of randlanet before reading this article. You can refer to the tf1.x version of RandLA-Net source code interpretation (5): testing. 

##  1.1, the dataset interface is converted to a placeholder 

 Randlanet uses the dataset interface to transfer data to the network, and in order to use the pb model, the data must be input into the computational graph in a feed_dict way, so the first step is to convert the dataset interface into a placeholder interface and save the model again. 

 We need to copy all the inference process code in the RandLANet.py, including inference (), dilated_res_block (), building_block (), relative_pos_encoding (), random_sample (), nearest_interpolation (), gather_neighbour (), att_pooling (). Where inference is the inference entrance and where we need to modify it. The original inference () is as follows 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 20240203095737331
  ```  
 Where inputs is the list of data output by dataset.flat_inputs, we need to split this list, set each array to 1 parameter, and then re-merge these arrays into a list inside inference, so that the following code does not need to be modified. As follows: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 20240203095737331
  ```  
 Next, we define the corresponding placeholders according to the order of the elements in the input list, and then reconstruct the computational graph to rewrite the trained weights into the new computational graph. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 20240203095737331
  ```  
 All the code is as follows, in addition to the inference () parameter list and the beginning of the need to modify, other code and RandLANet.py in the same code, no need to modify, in order to reduce space I will not write here. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 20240203095737331
  ```  
##  1.2、ckpt转pb 

 Get the CKPT model with feed_dict format as input and then convert it to pb format, which is relatively simple and goes directly to the code. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 20240203095737331
  ```  
##  1.3, pb test 

 Here we call the pb model to do a test, in which the data reading method is still using the dataset interface of tensorflow, refer to point cloud semantic segmentation: RandLANet model inference deployment, data preprocessing preprocess_pc () and dataset () classes are not modified. Modify the tester_Semantic3D.py, we recreate a tester_Semantic3D_pb.py. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 20240203095737331
  ```  
 Corresponding main function, refer to main_Semantic3D.py create main_Semantic3D_pb.py 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 20240203095737331
  ```  
#  Compile the corresponding version of TensorFlow 

 C++ dynamic link library for offline compilation of tensorflow 2.2.0 in windows environment 

#  reference 

 1、tensorflow ckpt to pb 



--------------------------------------------------------------------------------

#  Data reading and preprocessing 

##  1.1. Denoising and downsampling 

 denoising 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573732139
  ```  
 Downsampling 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573732139
  ```  
##  1.2. Pretreatment 

 Data preprocessing is code that simulates the enhancement in get_tf_map () in Python code and gets input information from each layer of the network coding layer. 

###  1.2.1, data enhancement 

 Refer to the article 3D point cloud transformation (translation, rotation, scaling) C++ implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573732139
  ```  
###  1.2.2, network input preparation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573732139
  ```  
#  Second, model reasoning 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573732139
  ```  
#  III. Result preservation 



--------------------------------------------------------------------------------

 After the model training is stable, the model is deployed. The dataset of RandLANet contains all the processes of training, verification, and testing. In actual deployment, we only need to do inference. At the same time, the output of RandLANet is just a label. We hope to be able to directly output the segmentation result with coordinates. 

#  First, data preprocessing 

 Modify on the basis of main_Semantic.py, add a new function preprocess_pc, that is, add the preprocessing process, and also add the operation of outlier removal, and modify the two downsampling to only do one downsampling. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573721484
  ```  
#  Ii. dataset 

 Also modify the training and validation data streams on the basis of main_Semantic.py, and only keep the test data streams. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573721484
  ```  
#  Third, the test 

 Reasoning results are written to the original point cloud. Modified on the basis of tester_Semantic3D.py 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573721484
  ```  
#  Iv. main 

 Integrate preprocessing, dataset, and test processes in main_Semantic.py. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573721484
  ```  


--------------------------------------------------------------------------------

