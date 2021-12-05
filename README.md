# Real-ESRGAN: Training Real-World Blind Super-Resolution with Pure Synthetic Data


## 目录

```
1. 简介
2. 数据集
3. 复现效果
4. 开始使用
5. 代码结构
6. 模型信息
```

## 1. 简介
![Real-ESRGAN](https://user-images.githubusercontent.com/52402835/144571624-a29d9a88-d08a-4891-8356-2d9d62798774.jpg)

本项目基于深度学习框架PaddlePaddle对Real-ESRGAN网络进行复现。Real-ESRGAN网络属于生成对抗网络，包括基于ESRGAN的生成器和基于U-Net的判别器，可对真实世界的复杂图像进行超分辨率重建。


**论文:** [Real-ESRGAN: Training Real-World Blind Super-Resolution with Pure Synthetic Data](https://paperswithcode.com/paper/real-esrgan-training-real-world-blind-super)

**参考repo:** [Real-ESRGAN](https://github.com/xinntao/Real-ESRGAN)

在此非常感谢` Xintao `贡献的[Real-ESRGAN](https://github.com/xinntao/Real-ESRGAN)的`Pytorch`代码，提高了本repo复现论文的效率。

**aistudio体验教程:** [地址](https://aistudio.baidu.com/aistudio/projectdetail/3156903)


## 2. 数据集

本项目训练所用的数据集为```DF2K```和```DF2K_multiscale```，它们是通过[DIV2K](http://data.vision.ee.ethz.ch/cvl/DIV2K/DIV2K_train_HR.zip)和[Flickr2K](https://cv.snu.ac.kr/research/EDSR/Flickr2K.tar)生成的，其中，```DF2K```包含3450张高分辨率图片，```DF2K_multiscale```包含13800张不同尺度下的低分辨率图片，我们将其放在[aistudio](https://aistudio.baidu.com/aistudio/datasetdetail/119372)上。

## 3. 复现效果
基于上述数据集的训练结果，在3张低分辨率图片上的测试结果如下：

![test_input1](inputs/00003.png)![test_input2](inputs/0014.jpg)![test_input3](inputs/0030.jpg)

<img src='results/00003_out.png' width = '513px'><img src='results/0014_out.jpg' width = '180px'><img src='results/0030_out.jpg' width = '220px'>

上面一行为测试输入图片，下面一行为测试输出图片。

上述测试所用的模型和训练日志可从[百度云网盘](https://pan.baidu.com/s/1mWO8aGCNdpRf8vXJIPjGYg)中下载，提取码：b8tl。

注：由于训练过程中网络中断，因此训练过程分为几段，```net_g_latest7.pdparams```为最后的权重结果。

## 4. 开始使用

### 4.1 准备环境

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

### 4.2 快速开始

**训练**


为了训练`Real-ESRGAN`模型，我们采用与原论文一致的初始化模型参数`ESRGAN_SRx4_DF2KOST_official-ff704c30.pth`，并将其转化为Paddle格式的权重`ESRGAN_SRx4_DF2KOST_official-ff704c30.pdparams`进行训练。
```
python train.py
```

**测试**

```
python inference_realesrgan.py
```

## 5. 代码结构

```
├─data                          
├─datasets                         
├─experiments                           
├─inputs       
├─loss
├─models
├─options
├─results
├─tb_logger
├─utils
│  README.md
│  inference_realesrgan.py                                                           
│  requirements.txt                                       
│  train.py                                     

```

## 6.模型信息
相关信息:

| 信息 | 描述 |
| --- | --- |
| 作者 | 勇敢土豆不怕困难！|
| 日期 | 2021年12月5日 |
| 框架版本 | PaddlePaddle==2.2.0 |
| 应用场景 | 超分辨率重建 |
| 硬件支持 | GPU、CPU |
| 在线体验 | [notebook](https://aistudio.baidu.com/aistudio/projectdetail/3156903)|
