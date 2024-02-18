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

