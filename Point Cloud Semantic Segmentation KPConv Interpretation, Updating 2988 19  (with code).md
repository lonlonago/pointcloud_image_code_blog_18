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

