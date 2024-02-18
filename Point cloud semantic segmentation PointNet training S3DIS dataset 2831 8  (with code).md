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

