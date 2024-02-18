 The last blog entry in the RandLANet series. 

 After the model training is stable, it is generally sampled C++ to formally deploy the environment, that is, to use C++ for forward reasoning. One reason is that the use of python deployment requires additional environment installation, which is not convenient for transplantation. The second is that the efficiency is not as good as C++. 

 When deploying a model with C++ version of TensorFlow, you typically do the following three steps: 

#  First, ckpt model to pb model 

 The key point of the ckpt to pb model is to know the name of the output node. This step can directly go to the training code to find the sess.run () sentence. sess.run () receives the return that is the name of the output node we need to do the model conversion. Directly print these variables to get the name of the output node we need. However, the randlanet used in this article is somewhat special in the process of converting the ckpt model to the pb model. Please make sure you have fully understood the testing process of randlanet before reading this article. You can refer to the tf1.x version of RandLA-Net source code interpretation (5): testing. 

##  1.1, the dataset interface is converted to a placeholder 

 Randlanet uses the dataset interface to transfer data to the network, and in order to use the pb model, the data must be input into the computational graph in a feed_dict way, so the first step is to convert the dataset interface into a placeholder interface and save the model again. 

 We need to copy all the inference process code in the RandLANet.py, including inference (), dilated_res_block (), building_block (), relative_pos_encoding (), random_sample (), nearest_interpolation (), gather_neighbour (), att_pooling (). Where inference is the inference entrance and where we need to modify it. The original inference () is as follows 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 20240203095737331
  ```  
 Where inputs is the list of data output by dataset.flat_inputs, we need to split this list, set each array to 1 parameter, and then re-merge these arrays into a list inside inference, so that the following code does not need to be modified. As follows: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 20240203095737331
  ```  
 Next, we define the corresponding placeholders according to the order of the elements in the input list, and then reconstruct the computational graph to rewrite the trained weights into the new computational graph. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 20240203095737331
  ```  
 All the code is as follows, in addition to the inference () parameter list and the beginning of the need to modify, other code and RandLANet.py in the same code, no need to modify, in order to reduce space I will not write here. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 20240203095737331
  ```  
##  1.2、ckpt转pb 

 Get the CKPT model with feed_dict format as input and then convert it to pb format, which is relatively simple and goes directly to the code. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 20240203095737331
  ```  
##  1.3, pb test 

 Here we call the pb model to do a test, in which the data reading method is still using the dataset interface of tensorflow, refer to point cloud semantic segmentation: RandLANet model inference deployment, data preprocessing preprocess_pc () and dataset () classes are not modified. Modify the tester_Semantic3D.py, we recreate a tester_Semantic3D_pb.py. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 20240203095737331
  ```  
 Corresponding main function, refer to main_Semantic3D.py create main_Semantic3D_pb.py 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 20240203095737331
  ```  
#  Compile the corresponding version of TensorFlow 

 C++ dynamic link library for offline compilation of tensorflow 2.2.0 in windows environment 

#  reference 

 1、tensorflow ckpt to pb 

