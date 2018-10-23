### SqueezeSeg: Convolutional Neural Nets with Recurrenct CRF for Real-time Road-Object Segmentation from 3D LiDAR Point Cloud
Point-wise classification problem
end-to-end pipeline

previous approaches comprise or use parts of the following stages: remove the ground, cluster the remaining points into instance, extract (hand-crafted) features from each cluster, and classify each cluster based on its features.

work with two-dimensional data considers raw images with projections of LiDAR point cloud top-down or from a number of other views.
other work considers three-dimensional data itself, discretizing the space into voxels and engineering features such as disparity, mean, saturation.

conditional random field (CRF) implemented as a recurrent layer
spherical projection to transform sparse
inspiration from SqueezeNet, a light-weight CNN that achieved AlexNet level accuracy with 50X fewer parameters
deconvolution modules(transposed convolutions) to up-sample feature maps in the width dimension
In order to reduce the number of model parameters and computation, we replaced convolution and deconvolution layers with fireModules and fireDeconvs

In order to obtain more training samples (both point clouds and point-wise labels), we built a LiDAR simulator in GTA-V, the framework of the simulator is based on DeepGTAV, which uses Scipt Hook V as a plugin.
We use ray casting to simulate each laser ray that LiDAR emits. The direction of each laser ray is based on several parameters of the LiDAR setup: vertical field of view (FOV), vertical resolution, pitch angle, and the index of the ray in the point cloud scan.

GTA-V does not encode a separate category for cyclists, instead marking people and vehicles separately on all accounts. For these reasons, we decided to focus on the 'car' class for KITTI evaluation when training with our synthesized dataset.

Velodyne HDL-64E LiDAR with 64 vertical channels, so H=64. front view area of 90 and divide it into 512 grids so W=512. 
Use 5 features for each point, 3 cartesian coordinates (x,y,z), an intensity measurement and range r=(x^2+y^2+z^2)^0.5.

types: unknow car pedestrian cyclist



### SqueezeNet: AlexNet-level accuracy with 50x fewer parameters and <0.5mb model size
SqueezeNet网络基本单元是采用了模块化的卷积，其称为Fire module，Fire模块主要包含两层卷积操作，一是采用1x1卷积核的squeeze层，二是混合使用1x1和3x3卷积核的expand层。



