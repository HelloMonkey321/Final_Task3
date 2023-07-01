# Final_Task3  
本实验使用具有泛化能力的NeRF模型对物体进行三维重建，NeRF工作的过程可以分成三部分：三维重建、渲染和训练。  
1. 三维重建部分本质上是一个2D到3D的建模过程，利用三维位置(x，y，z)和二维方位视角(θ，φ)作为输入，输出是颜色c=(r，g，b)和体素密度(σ)，主要是通过利用多层感知机（MLP）网络建模来近似地表示输入与输出的映射关系，形成了3D场景的“隐式表示”。
2. 渲染部分本质上是一个3D到2D的建模过程，渲染部分利用重建部分得到的3D点的颜色及体素密度沿着光线进行整合得到最终的2D图像像素值。该部分使用经典体渲染（Volume Rendering）的原理渲染通过场景的任何光线的颜色。
3. 在训练部分，主要是利用渲染部分得到的2D图像，通过与Ground Truth做损失函数L2进行网络优化。
