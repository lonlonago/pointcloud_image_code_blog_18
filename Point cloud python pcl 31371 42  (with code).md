PCL (Point Cloud Library) is a large cross-platform open-source C++ programming library established on the basis of absorbing previous research on point clouds. It realizes a large number of general algorithms and efficient data structures related to point clouds, involving point cloud acquisition, filtering, segmentation, registration, retrieval, feature extraction, recognition, tracking, surface reconstruction, visualization, etc. It supports a variety of operating system platforms and can run on Windows, Linux, Android, Mac OS X, and some embedded real-time systems. If OpenCV is the crystallization of 2D information acquisition and processing, then PCL has the same status in 3D information acquisition and processing. PCL is a BSD authorization method and can be used for commercial and academic applications for free 

 ![avatar]( aHR0cDovL2ltZy5ibG9nLmNzZG4ubmV0LzIwMTcxMjA2MTAyOTI5OTU5) 

 Ubuntu under the PCL official installation method is: sudo add-apt-repository ppa: v-launchpad-jochen-sprickerhof-de/pcl sudo apt-get update sudo apt-get install libpcl-all is very simple, then the Python PCL library installation is also a tutorial, but compared to the C++ library is relatively small, the routine is relatively small, so, today will not demonstrate, the operation of interested students can query the URL https://github.com/strawlab/python-pcl 

 https://www.quora.com/How-do-I-install-PCL-for-Python-in-Windows operation, the specific instructions are as follows: Introduction 

 This is a small python binding to the pointcloud library. Currently, the following parts of the API are wrapped (all methods operate on PointXYZ) point types 

 I/O and integration; saving and loading PCD files segmentation SAC smoothing filtering registration (ICP, GICP, ICP_NL) 

 The code tries to follow the Point Cloud API, and also provides helper function for interacting with NumPy. For example (from tests/test.py) 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573747740
  ```  
 or, for smoothing 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573747740
  ```  
 Point clouds can be viewed as NumPy arrays, so modifying them is possible using all the familiar NumPy functionality: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573747740
  ```  
 More samples can be found in the examples directory, and in the unit tests. 

 This work was supported by Strawlab. 

 Requirements 

 This release has been tested on Linux Ubuntu 14.04 with 

 Python 2.7.6, 3.4.0, 3.5.2 pcl 1.7.0 Cython <= 0.25.2 and MacOS with 

 Python 2.7.6, 3.4.0, 3.5.2 pcl 1.8.1(use homebrew) Cython <= 0.25.2 and Windows with 

 (Miniconda/Anaconda) - Python 3.4 pcl 1.6.0(VS2010) Cython <= 0.25.2 Gtk+ and Windows with 

 (Miniconda/Anaconda) - Python 3.5 pcl 1.8.0(VS2015) Cython <= 0.25.2 Gtk+ Installation 

 Linux (Ubuntu) 

 PCL 1.7.0(use apt-get) 

 Install PCL Module. sudo add-apt-repository ppa:v-launchpad-jochen-sprickerhof-de/pcl -y 

 sudo apt-get updated -and 

 sudo apt-get install libpcl-all -y PCL 1.8.0 (build module)([CI Test Timeout]) 

 Build Module 

 Reference here. MacOSX 

 use homebrew 

 Install PCL Module. brew tap homebrew/science 

 brew install pcl Warning: 

 Current Installer (2017/10/02) Not generated pcl-2d-1.8.pc file.(Issue #119) 

 Reference PointCloudLibrary Issue. 

 Pull qequests 1679. 

 Issue 1978. circumvent: 

 copy travis/pcl-2d-1.8.pc file to /usr/local/lib/pkgconfig folder. Windows 

 before Install module 

 Case1. use PCL 1.6.0 

 Windows SDK 7.1 PCL All-In-One Installer 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573747740
  ```  
 Common setting 

 pip module install. pip install --upgrade pip 

 pip install cython = =0.25.2 

 pip install numpy instal python module python setup.py build_ext -i 

 python setup.py install Build & Test Status 

 windows(1.6.0/1.8.1) 

 Mac OSX (1.8.1)/Ubuntu14.04 (1.7.0) 

 A note about types 

 Point Cloud is a heavily templated API, and consequently mapping this into Python using Cython is challenging. 

 It is written in Cython, and implements enough hard bits of the API (from Cythons perspective, i.e the template/smart_ptr bits) to provide a foundation for someone wishing to carry on. 

 API Documentation 

 For deficiencies in this documentation, please consult the PCL API docs, and the PCL tutorials. 

 The above is the information I have integrated, so installing the Python PCL library is very simple, but there are relatively few routines. If you are interested, you can study it yourself. If you have any friends who study Python at the same time, please share it actively. Follow the WeChat official account, or join the QQ group to communicate and share! 

