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

