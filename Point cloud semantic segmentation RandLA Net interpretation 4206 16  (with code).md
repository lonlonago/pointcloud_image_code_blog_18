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

