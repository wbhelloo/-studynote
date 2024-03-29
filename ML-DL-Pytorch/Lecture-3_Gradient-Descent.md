## ML/DL for Everyone with Pytorch

## Lecture 3_Gradient Descent

线性回归的损失函数定义：

$$ loss = (\hat{y}-y)^2 = (x*w-y)^2 $$

关于w的导数该如何计算？

$$ \frac{\partial{loss}}{\partial{w}}=? $$

利用数学原理计算如下：

$$ \frac{d}{dx}[f(x)]=f'(x)=2w(wx-y) $$

Pytorch代码实现

```python
import numpy as np
import matplotlib.pyplot as plt

x_data = [1.0, 2.0, 3.0]
y_data = [2.0, 4.0, 6.0]

w = 1.0  # a random guess: random value

# our model forward pass
def forward(x):
   return x * w


# Loss function
def loss(x, y):
   y_pred = forward(x)
   return (y_pred - y) * (y_pred - y)


# compute gradient
def gradient(x, y):  # d_loss/d_w
   return 2 * x * (x * w - y)

# Before training
print("predict (before training)",  4, forward(4))

# Training loop
for epoch in range(100):
   for x_val, y_val in zip(x_data, y_data):
       grad = gradient(x_val, y_val)
       w = w - 0.01 * grad
       print("\tgrad: ", x_val, y_val, grad)
       l = loss(x_val, y_val)

   print("progress:", epoch, "w=", w, "loss=", l)

# After training
print("predict (after training)",  "4 hours", forward(4))
```

