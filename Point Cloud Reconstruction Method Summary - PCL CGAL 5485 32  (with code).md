#  I. Introduction 

 A few days ago, I took the time to run the common reconstruction methods in PCL and CGAL, and I will summarize them here today. 

 First, the main methods: 

 II. Data: 

 Take bunny data as an example to show the reconstruction effect  

#  Effect display 

##  2.1 Implemented in PCL 

 1. Convex hull reconstruction 

 ![avatar]( 66890e80133f4857a01ebabe48713e2f.png) 

 2. Concave bag reconstruction 

 ![avatar]( a7ea9a19a24540e2b73084ecaa0e6648.png) 

 Alpha=0.5  

 ![avatar]( ceaebe14915a475f837faf3838a701ac.png) 

 Alpha=1.5  Alpha=5  

 ![avatar]( 4a95ea0a406747b4ad41cb41c09e5586.png) 

 Alpha=15  

 3. Greedy reconstruction 

 ![avatar]( e520290204214407962b9863f4865912.png) 

 4. Poisson Reconstruction 

 ![avatar]( 244fbd3c0e7c45dabd535c2abb66ea7e.png) 

##  2.2 Implementation in CGAL 

 1. The reconstruction process in CGAL is as follows 

 ![avatar]( 6442e2f65d504b1fbdcfba3e5aa2db07.png) 

  2. Reconstruction effect in CGAL 

 ![avatar]( 5acc590088694472a23d9de2cb01a527.png) 

 ![avatar]( 02c448eda527447ba2a9ee296187c491.png) 

 ![avatar]( 9cda6bfe9a1346c88baecefb8e2f7053.png) 

#  III. Follow-up 

 The code will be released or integrated into QT + PCL later. 

