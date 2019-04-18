## Win10安装Tensorflow（GPU版本）

### 1, 查看gpu是否支持cuda

例如：geforce-gtx-960: 

[https://www.geforce.com/hardware/desktop-gpus/geforce-gtx-960/specifications](https://www.geforce.com/hardware/desktop-gpus/geforce-gtx-960/specifications)

### 2, 安装cuda.

CUDA Toolkit 9.0下载链接：

[https://developer.nvidia.com/cuda-90-download-archive?target_os=Windows&target_arch=x86_64&target_version=10&target_type=exelocal](https://developer.nvidia.com/cuda-90-download-archive?target_os=Windows&target_arch=x86_64&target_version=10&target_type=exelocal)

### 3, 验证cuda是否安装成功

cmd: `nvcc --version`

```linux
C:\Users\Ruishao>nvcc --version
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2017 NVIDIA Corporation
Built on Fri_Sep__1_21:08:32_Central_Daylight_Time_2017
Cuda compilation tools, release 9.0, V9.0.176
```

### 4, 下载cuda对应版本的cuDNN

- 下载cuDNN7.0

    [https://developer.nvidia.com/cudnn](https://developer.nvidia.com/cudnn)

    > 下载cuDNN需要注册会员(免费)。

- 安装cuDNN

    > 请参考：[https://blog.csdn.net/weixin_39579513/article/details/79434309](https://blog.csdn.net/weixin_39579513/article/details/79434309),六,安装cuDNN7.0部分

### 5， 查看tensorflow支持的cuda版本，安装对应tensorflow-gpu.

[https://www.tensorflow.org/install/source_windows](https://www.tensorflow.org/install/source_windows)

`pip install --ignore-installed --upgrade tensorflow_gpu==1.10.0`

### 6，ok

> 参考：[https://zhuanlan.zhihu.com/p/37086409](https://zhuanlan.zhihu.com/p/37086409)
