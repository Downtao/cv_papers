### Deformable ConvNets v2: More Deformable, Better Results

#### 摘要

​		可变形卷积网络的卓越性能源于其适应对象几何变化的能力。通过检查其适应性行为，我们观察到，尽管其神经特征的空间支持比常规的ConvNets更紧密地符合对象结构，但这种支持可能仍远远超出了感兴趣区域，从而导致特征受无关图像内容的影响 。为了解决这个问题，我们提出了可变形卷积的一种重新设计，它通过提高建模能力和更强的训练来提高卷积关注相关图像区域的能力。通过网络中可变形卷积的更全面集成，以及通过引入扩展变形建模范围的调制机制，可以增强建模能力。为了有效地利用这种丰富的建模能力，我们通过提出的特征模仿方案来指导网络训练，该方案可以帮助网络学习反映目标焦点和RCNN特征分类能力的特征。通过提议的贡献，此新版本的Deformable ConvNets在原始模型上获得了显着的性能提升，并在COCO基准测试的对象检测和实例分割中产生了领先的结果。

#### 1. 引言

​		有尺度、姿态、视角和部分形变引起的几何变化是目标识别和检测的主要挑战。当前处理这个问题的最佳方法是可变形卷积网络（DCNv1），其引入了两个模块，可帮助CNN对此类变化进行建模。这些模块之一是可变形卷积，其中标准卷积的网格采样位置对于先前的特征图学习了位移。另一个是可变形的RoIPooling，其中偏移是在RoIPooling的bin位置中学习得到的。将这些模块整合到神经网络后，它就可以使其特征表示适应目标的配置，特别是通过变形其采样和合并模式以适合目标的结构。利用这一方法，目标检测准确率获得很大的提升。

​		为了理解可变形卷积网络，作者通过排列PASCAL VOC图像中的偏移采样位置来可视化感受野中的感应变化[11]。