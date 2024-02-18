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

