
# 2023-3

## Day 9 
I briefly survey some interpolation approaches in the deep latent space. My short-term goal is to find a reliable unsupervised point cloud interpolation method in which the semantic manipulation can be conducted. 

### 1.Intrinsic Point Cloud Interpolation via Dual Latent Space Navigation, ECCV 2020;
![图片](https://user-images.githubusercontent.com/49975503/224021199-86deb042-b11f-4a8e-8041-d8077bd23090.png)
This work claims that the AE focuses on the reconstruction task while the latent space is not capable of linear interpolation. However, we can define some consecutive interpolation energy for mesh-based data. Thus, we can parallel the PC AE with a Mesh-edges AE, the Mesh-edges AE is regularized via traditional interpolation energy to enhance the structral information in the latent space. 

Q1: what is the relationship between local 【more instance-wise geodesic aware】 & global 【more structural latent space】?
  
G1: I guess if the encoder can capture the geodesic well, the morphing will be more smooth, leads to more structural latent space. 
  
### 2.IDEA-Net: Dynamic 3D Point Cloud Interpolation via Deep Embedding Alignment, 2022;
![图片](https://user-images.githubusercontent.com/49975503/224030723-da1ec42c-7d72-4f22-a502-f5f6ad1e9bc3.png)
Different from 1, this work is a supervised method for point cloud frame interpolation based on scene flow. The core of this method is to decompose the complicated scene flow into 【linear flow】 and 【non-linear flow residual】. For the non-linear part, it linearizes it by embedding the point into high-dimensional feature space. 

Key1: The learned 【soft correspondence】 based on feature distances is useful!

Key2: The parallel from  $t$ from $0 \rightarrow 1$ & $1 \rightarrow 0$ formulates a natural regularizer for the time interpolation or shape homotopy.

Intuition1: work1 is high-level manipulation, work 2 is low-level manipulation, however, work2 also seeks for high-level features to capture the non-linear geodesic.

### 3.LATENT IMAGE ANIMATOR: LEARNING TO ANIMATE IMAGES VIA LATENT SPACE NAVIGATION, ICLR 2022;
![图片](https://user-images.githubusercontent.com/49975503/224035549-c00d41f2-ab92-4f38-8d09-defce7eba6e3.png)

This work find a set of 【orthogonal basis in the latent space】, each direction captures a kind of morphing.

### 4.On Linear Interpolation in the Latent Space of Deep Generative Models， ICLR 2021; *
![图片](https://user-images.githubusercontent.com/49975503/224036036-2497bf59-c2bc-4fbb-8b4e-4b61b8ee8a5f.png)
This work proposes a method to capture how is the geodesics in the latent space apart from the straight line. There are many interesting details in this work, like:

Key1: how to get the 【pull-back metric】& geodesic, why optimization method rather than geodesic ODE.

Key2: use B-splines to parameterize the geodesic, local controllable. 

TODO: I should explore the details in this work & some references. 
