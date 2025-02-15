# Homework 4: Auto Encoder

# Task

Please write an auto-encoder for the images.

- Use the trained encoder to obtain the 2-dimensional code of the **last 1000 images** in the test set, and visualize them with a scatterplot where different colors represent different digits.
- Use the decoder to generate 20 images by sampling some codes.

# Dataset

- Download: http://yann.lecun.com/exdb/mnist/
- The dataset consists of a training set and test set of images. Each image is a handwritten digit.
- You can process the dataset according to the guidelines in this website: https://www.jianshu.com/p/84f72791806f

# Submitted files

- **Source code (pytorch)**: It should include at least two programming files, namely auto_encoder.py, decoder_generate.py.
- **encoder.png** : a scatterplot for visualizing the 2-dimensional code of the last 1000 images in the test set. Please use different colors to represent different digits.
- A file directory named **imgs_generated**: the file directory contains 20 images generated by the decoder.
- **Report.pdf**: Please describe the configurations for running your code, and provide some analysis for the results in your report with no more than 2 pages.

# Implementation

## 整体概述

1.数据集：MNIST 手写数字数据集，包含 60000 个训练数据，10000 个测试数据，其中图片像素为 28×28，通道数量为 1。

2.数据格式：

- train_images：ndarray:60000,28,28
- train_labels：ndarray:60000,
- test_images：ndarray:10000,28,28
- test_labels：ndarray:10000,

  3.实验目标：

- 编写`auto_encoder.py`，读取测试数据集中最后 1000 个数据，编码为 2 维向量，并画出散点图，每个数字用不同颜色标注出来，保存为 encoder.png 图片。
- 编写`decoder_generate.py`，采集 20 个编码并复原图像，保存到 imgs_generated 文件夹。

## 项目结构

![Auto-Encoder](https://zhoujianan.com/assets/school/FDU_Course_ML/4.Auto%20Encoder/Auto-Encoder.png)

## Auto-Encoder

1.实验日志：

```
epoch 0: L_tot 161.47 L_likelihood -157.01 L_divergence 4.46
epoch 1: L_tot 160.73 L_likelihood -155.26 L_divergence 5.47
……………………………………………………………………
epoch 59: L_tot 129.28 L_likelihood -122.03 L_divergence 7.25
```

2.散点图：可以看出随着 epoch 的增多，分类效果逐渐变好。
![epoch](https://zhoujianan.com/assets/school/FDU_Course_ML/4.Auto%20Encoder/epoch.png)

## Auto-Decoder

1.实验日志：

```
epoch 0: L_tot 129.55 L_likelihood -113.06 L_divergence 16.49
epoch 1: L_tot 113.52 L_likelihood -93.73 L_divergence 19.79
……………………………………………………………………
epoch 19: L_tot 103.72 L_likelihood -80.75 L_divergence 22.97
```

2.复原图：为了展示美观，这里选取了 100 个样本进行复原，并将每次迭代后的结果进行展示，可以清晰地看到，随着 epoch 的增多，复原效果也越来越好。

![decoder](https://zhoujianan.com/assets/school/FDU_Course_ML/4.Auto%20Encoder/decoder.png)
