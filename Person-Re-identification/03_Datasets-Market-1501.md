### Person Re-identification数据集_Market-1501介绍

#### 数据集简介

> Zheng, Liang, et al. “Scalable Person Re-identification: A Benchmark.” IEEE International Conference on Computer Vision IEEE Computer Society, 2015:1116-1124.

- Market-1501 数据集在清华大学校园中采集，夏天拍摄，在 2015 年构建并公开。

- 它包括由`6`个摄像头（其中`5`个高清摄像头和`1`个低清摄像头）拍摄到的 `1501` 个行人、`32668` 个检测到的行人矩形框。每个行人至少由 2 个摄像头捕获到，并且在一个摄像头中可能具有多张图像。

- 训练集有 `751` 人，包含 `12,936` 张图像，平均每个人有 `17.2` 张训练数据；

- 测试集有 `750` 人，包含 `19,732` 张图像，平均每个人有 `26.3` 张测试数据。

- `3368` 张查询图像的行人检测矩形框是人工绘制的，而 `gallery` 中的行人检测矩形框则是使用DPM检测器检测得到的。

#### 目录结构

    Market-1501
    　　├── bounding_box_test
    　　　　　　　├── 0000_c1s1_000151_01.jpg
    　　　　　　　├── 0000_c1s1_000376_03.jpg
    　　　　　　　├── 0000_c1s1_001051_02.jpg
    　　├── bounding_box_train
    　　　　　　　├── 0002_c1s1_000451_03.jpg
    　　　　　　　├── 0002_c1s1_000551_01.jpg
    　　　　　　　├── 0002_c1s1_000801_01.jpg
    　　├── gt_bbox
    　　　　　　　├── 0001_c1s1_001051_00.jpg
    　　　　　　　├── 0001_c1s1_009376_00.jpg
    　　　　　　　├── 0001_c2s1_001976_00.jpg
    　　├── gt_query
    　　　　　　　├── 0001_c1s1_001051_00_good.mat
    　　　　　　　├── 0001_c1s1_001051_00_junk.mat
    　　├── query
    　　　　　　　├── 0001_c1s1_001051_00.jpg
    　　　　　　　├── 0001_c2s1_000301_00.jpg
    　　　　　　　├── 0001_c3s1_000551_00.jpg
    　　└── readme.txt

#### 目录介绍

- `bounding_box_test`--用于测试集的 `750` 人，包含 `19,732` 张图像; 前缀为 `0000` 表示在提取这 `750` 人的过程中`DPM`检测错的图（可能与`query`是同一个人），`-1` 表示检测出来其他人的图（不在这 `750` 人中）。

- `bounding_box_train`--用于训练集的 `751` 人，包含 `12,936` 张图像。

- `query`--为 `750` 人在每个摄像头中随机选择一张图像作为 `query`，因此一个人的`query`最多有 `6` 个，共有 `3,368` 张图像。

- `gt_query`--`matlab`格式，用于判断一个`query`的哪些图片是好的匹配（同一个人不同摄像头的图像）和不好的匹配（同一个人同一个摄像头的图像或非同一个人的图像）。

- `gt_bbox`--手工标注的 `bounding box`，用于判断`DPM`检测的`bounding box`是不是一个好的`box`。

#### 命名规则

- 以 `0001_c1s1_000151_01.jpg` 为例

    1). `0001` 表示每个人的标签编号，从`0001`到`1501`；

    2). `c1` 表示第一个摄像头`(camera1)`，共有`6`个摄像头；

    3). `s1` 表示第一个录像片段`(sequece1)`，每个摄像机都有数个录像段；

    4). `000151` 表示 `c1s1` 的第`000151`帧图片，视频帧率`25fps`；

    5). `01` 表示 `c1s1_001051` 这一帧上的第`1`个检测框，由于采用`DPM`检测器，对于每一帧上的行人可能会框出好几个`bbox`; `00` 表示手工标注框。

    
#### 数据集下载

- [Google Drive](https://drive.google.com/file/d/0B8-rUzbwVRk0c054eEozWG9COHM/view)

- [Baidu Drive](https://pan.baidu.com/s/1ntIi2Op)

