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

