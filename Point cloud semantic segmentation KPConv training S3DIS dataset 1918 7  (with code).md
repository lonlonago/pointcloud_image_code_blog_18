The code uses the github project provided by the KPconv author. 

##  KPConv training S3DIS dataset 

 1. Data preparation, this part refers to RandLA-Net training S3DIS dataset 2. Compile C++ code, compile method refers to INSTALL.md, divided into linux and win10 systems. Find the cpp_wrappers folder under the Ubuntu system and execute it directly in the end point 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573775433
  ```  
 In the win10 system, compile cpp_neighbors and cpp_subsampling separately, execute 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573775433
  ```  
 and 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573775433
  ```  
 I myself in the win10 system under the test found that the execution of build.bat will prompt no py command, if you also encounter the same problem, you can follow the following operation to compile, compile cpp_neighbors, under cmd into the cpp_warppers\ cpp_neighbors folder, execute the following statement 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573775433
  ```  
 The method of compiling cpp_subsampling is the same as above. 

 3. To train the model, modify the data address before training, in line 88 of the datasets\ S3DIS.py script 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573775433
  ```  
 The S3DIS dataset has a total of 6 regions of data, namely Area_1, Area_2, Area_3, Area_4, Area_5, Area_6. The author uses Area_5 as the test set and the other 5 regions as the training dataset. See code datasets\ S3DIS.py line 114 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573775433
  ```  
 Then start training the model 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573775433
  ```  
