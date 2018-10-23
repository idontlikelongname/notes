### SqueezeSeg: Convolutional Neural Nets with Recurrenct CRF for Real-time Road-Object Segmentation from 3D LiDAR Point Cloud
Point-wise classification problem
end-to-end pipeline
conditional random field (CRF) implemented as a recurrent layer
spherical projection to transform sparse
inspiration from SqueezeNet, a light-weight CNN that achieved AlexNet level accuracy with 50X fewer parameters
deconvolution modules(transposed convolutions) to up-sample feature maps in the width dimension
In order to reduce the number of model parameters and computation, we replaced convolution and deconvolution layers with fireModules and fireDeconvs

In order to obtain more training samples (both point clouds and point-wise labels), we built a LiDAR simulator in GTA-V, the framework of the simulator is based on DeepGTAV, which uses Scipt Hook V as a plugin.
We use ray casting to simulate each laser ray that LiDAR emits. The direction of each laser ray is based on several parameters of the LiDAR setup: vertical field of view (FOV), vertical resolution, pitch angle, and the index of the ray in the point cloud scan.

GTA-V does not encode a separate category for cyclists, instead marking people and vehicles separately on all accounts. For these reasons, we decided to focus on the 'car' class for KITTI evaluation when training with our synthesized dataset.



### SqueezeNet: AlexNet-level accuracy with 50x fewer parameters and <0.5mb model size



### AlexNet
2012年提出的网络结果，赢得了2012届图像识别大赛的冠军，使得CNN成为在图像分类上的核心算法模型


### VGGNet
#### OverFeat 
全连接层替换为卷积层，使得测试得到的全卷积网络因为没有全连接的限制，因而可以接收任意宽或高的输入
全连接转卷积的方法，可以来处理任意分辨率上的计算卷积，无需对原图做缩放处理
VGG16 VGG19

