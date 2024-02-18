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
