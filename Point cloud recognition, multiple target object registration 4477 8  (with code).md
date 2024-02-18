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

