## ML/DL for Everyone with Pytorch

## Lecture 1: Overview

### Goals

- Basic understanding of machine learning/deep learning

- PyTorch implementation skills 

--- 

补充知识：

> 摘自：[https://pytorch.apachecn.org](https://pytorch.apachecn.org)

### 什么是PyTorch？

PyTorch是一个基于python的科学计算包，作为NumPy的替代品，可以利用GPU的性能进行计算。

### 基础知识

- 张量(Tensor)

    Tensor（张量）类似于NumPy的ndarray，但可以在GPU上使用，实现加速计算。

    1. `torch.rand()`创建一个随机初始化矩阵：

        ```python
        x = torch.rand(5, 3)
        print(x)

        # 
        tensor([[0.8346, 0.1771, 0.4382],
            [0.2016, 0.4509, 0.4740],
            [0.6760, 0.6652, 0.4058],
            [0.5359, 0.2559, 0.1360],
            [0.0284, 0.5848, 0.3186]])
        ```

    2. `.size()` 获取它的形状

        ```python
        print(x.size())

        # 
        torch.Size([5, 3])
        ```

        > `torch.Size`本质上还是`tuple`，所以支持`tuple`的一切操作。

    3. `torch.randn_like(x, dtype=torch.float)`构建一个和 x 相同大小的随机初始化矩阵。

        ```python
        z = torch.randn_like(x, dtype=torch.float)
        print(z)

        # 
        tensor([[ 0.9789, -0.9387,  0.1610],
            [ 0.3073,  1.0681, -0.9156],
            [-1.8072, -0.1307, -0.7662],
            [-0.1763,  0.8565,  1.6717],
            [-0.1602,  0.5948,  0.0871]])
        ```

- 运算

    加法：

    1. `torch.add(x, y)` 

    2. 给定一个输出张量作为参数 `torch.add(x, y, out=result)`

    改变形状 `torch.view`

    ```python
    y = z.view(15,1)
    print(y)

    #
    tensor([[ 0.9789],
    [-0.9387],
    [ 0.1610],
    [ 0.3073],
    [ 1.0681],
    [-0.9156],
    [-1.8072],
    [-0.1307],
    [-0.7662],
    [-0.1763],
    [ 0.8565],
    [ 1.6717],
    [-0.1602],
    [ 0.5948],
    [ 0.0871]])
    ```

    ```python
    print(z.shape)
    print(y.shape)

    # 
    torch.Size([5, 3])
    torch.Size([15, 1])
    ```

- 和Numpy转换 `torch.from_numpy(x)`

    ```python
    import numpy as np
    x = np.ones((3,3))
    a = torch.from_numpy(x)
    print(a)

    tensor([[1., 1., 1.],
            [1., 1., 1.],
            [1., 1., 1.]], dtype=torch.float64)
    ```

- CUDA上的张量

    张量可以使用.to方法移动到任何设备（device）上：

    ```python
    x = torch.rand(5, 3)

    # let us run this cell only if CUDA is available
    # 我们将使用`torch.device`来将tensor移入和移出GPU
    if torch.cuda.is_available():
        device = torch.device("cuda")          # a CUDA device object
        y = torch.ones_like(x, device=device)  # 直接在GPU上创建tensor
        x = x.to(device)                       # 或者使用`.to("cuda")`方法
        z = x + y
        print(z)
        print(z.to("cpu", torch.double))       # `.to`也能在移动时改变dtype

    #
    tensor([[1.2425, 1.0937, 1.8771],
            [1.2003, 1.8379, 1.2503],
            [1.6172, 1.7879, 1.7782],
            [1.3666, 1.3225, 1.9927],
            [1.3918, 1.8958, 1.8816]], device='cuda:0')
    tensor([[1.2425, 1.0937, 1.8771],
            [1.2003, 1.8379, 1.2503],
            [1.6172, 1.7879, 1.7782],
            [1.3666, 1.3225, 1.9927],
            [1.3918, 1.8958, 1.8816]], dtype=torch.float64)   
    ``` 



