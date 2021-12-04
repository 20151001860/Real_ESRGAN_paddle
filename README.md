# Real-ESRGAN: Training Real-World Blind Super-Resolution with Pure Synthetic Data


## 目录

```
1. 简介
2. 数据集和复现精度
3. 开始使用
4. 代码结构与详细说明
```

## 1. 简介
![Real-ESRGAN](https://user-images.githubusercontent.com/52402835/144571624-a29d9a88-d08a-4891-8356-2d9d62798774.jpg)

本项目基于深度学习框架PaddlePaddle对Real-ESRGAN网络进行复现。Real-ESRGAN网络属于生成对抗网络，包括基于ESRGAN的生成器和基于U-Net的判别器，可对真实世界的复杂图像进行超分辨率重建。


**论文:** [Real-ESRGAN: Training Real-World Blind Super-Resolution with Pure Synthetic Data](https://paperswithcode.com/paper/real-esrgan-training-real-world-blind-super)

**参考repo:** [Real-ESRGAN](https://github.com/xinntao/Real-ESRGAN)

在此非常感谢` Xintao `贡献的[Real-ESRGAN](https://github.com/xinntao/Real-ESRGAN)的`Pytorch`代码，提高了本repo复现论文的效率。

**aistudio体验教程:** [地址](url)


## 2. 数据集准备

本项目训练所用的数据集为[DIV2K](http://data.vision.ee.ethz.ch/cvl/DIV2K/DIV2K_train_HR.zip)，[Flickr2K](https://cv.snu.ac.kr/research/EDSR/Flickr2K.tar)和[OST](https://openmmlab.oss-cn-hangzhou.aliyuncs.com/datasets/OST_dataset.zip)。

|数据集|大小|下载链接|数据格式|
| :---: | :---: | :----: |:----: |
|DIV2K|120k|[DIV2K](http://data.vision.ee.ethz.ch/cvl/DIV2K/DIV2K_train_HR.zip)|`png`|
|Flickr2K|120k|[Flickr](https://cv.snu.ac.kr/research/EDSR/Flickr2K.tar)|`png`|
|OST|120k|[OST](https://openmmlab.oss-cn-hangzhou.aliyuncs.com/datasets/OST_dataset.zip)|`png`|

### 2.1 产生多尺度图片

### 2.2 裁剪成子图片

基于上述数据集，给出论文中精度、参考代码的精度、本repo复现的精度、数据集名称、模型下载链接（模型权重和对应的日志文件推荐放在**百度云网盘**中，方便下载）、模型大小，以表格的形式给出。如果超参数有差别，可以在表格中新增一列备注一下。

如果涉及到`轻量化骨干网络验证`，需要新增一列骨干网络的信息。



## 3. 开始使用

### 3.1 准备环境

- 硬件：Tesla V100 GPU
- 框架：PaddlePaddle >= 2.2.0


**克隆本项目**
```
# clone this repo
git clone https://github.com/20151001860/Real_ESRGAN_paddle.git
cd Real_ESRGAN_paddle

```
**安装第三方库**

```
pip install -r requirements.txt
```
然后介绍下怎样安装PaddlePaddle以及对应的requirements。

建议将代码中用到的非python原生的库，都写在requirements.txt中，在安装完PaddlePaddle之后，直接使用`pip install -r requirements.txt`安装依赖即可。


### 3.2 快速开始

**训练**


为了训练`Real-ESRGAN`模型，我们采用与原论文一致的初始化模型参数`ESRGAN_SRx4_DF2KOST_official-ff704c30.pth`，并将其转化为Paddle格式的权重`ESRGAN_SRx4_DF2KOST_official-ff704c30.pdparams`进行训练。
```
python train.py
```
训练保存的模型和日志可见：

**测试**

```
python inference_realesrgan.py
```
测试使用7张图片，结果如下：

需要给出快速训练、预测、使用预训练模型预测、模型导出、模型基于inference模型推理的使用说明，同时基于demo图像，给出预测结果和推理结果，并将结果打印或者可视化出来。

## 4. 代码结构与详细说明

### 4.1 代码结构

需要用一小节描述整个项目的代码结构，用一小节描述项目的参数说明，之后各个小节详细的描述每个功能的使用说明。

### 4.2 参数说明

以表格的形式，给出当前的参数列表、含义、类型、默认值等信息。

### 4.3 基础使用

配合部分重要配置参数，介绍模型训练、评估、预测、导出等过程。

### 4.4 模型部署

给出当前支持的推理部署方式以及相应的参考文档链接。

### 4.5 TIPC测试支持

这里需要给出TIPC的目录链接。

**注意：** 这里只需提供TIPC基础测试链条中模式`lite_train_lite_infer`的代码与文档即可。


* 更多关于TIPC的介绍可以参考：[飞桨训推一体认证（TIPC）文档](https://github.com/PaddlePaddle/PaddleOCR/blob/dygraph/test_tipc/readme.md)
* 关于Linux端基础链条测试接入的代码与文档说明可以参考：[基础链条测试接入规范](https://github.com/PaddlePaddle/models/blob/tipc/docs/tipc_test/development_specification_docs/train_infer_python.md)，[PaddleOCR Linux端基础训练预测功能测试文档](https://github.com/PaddlePaddle/PaddleOCR/blob/dygraph/test_tipc/docs/test_train_inference_python.md)


如果您有兴趣，也欢迎为项目集成更多的TIPC测试链条及相关的代码文档，非常感谢您的贡献。
