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

