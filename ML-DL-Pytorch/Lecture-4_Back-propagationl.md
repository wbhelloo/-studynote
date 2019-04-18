# ML/DL for Everyone with Pytorch

## Lecture 4_Back propagationl

1. Computing gradient in simple network

    简单的网络我们可以通过数学运算计算关于W的导数。

    $$ x \longrightarrow Linear \longrightarrow \hat {y} $$  

    $$ \frac{\partial{loss}}{\partial{w}}=? $$

    $$ \frac{d}{dx}[f(x)]=f'(x)=2x(xw-y) $$

    ```python
    # compute gradient
    def gradient(x, y):  # d_loss/d_w
        return 2 * x * (x * w - y)
    ```

2. Complicated network?

    如果对于一个复杂的网络，我们还能通过数学运算计算导数吗？

    ![Deep Neural Network](http://www.ruanyifeng.com/blogimg/asset/2017/bg2017071201.jpg)

    Gradient of loss with respect to w

    $$ \frac{\partial{loss}}{\partial{w}}=? $$

    Better way? Computational graph + chain rule

    Chain Rule?

    $$ f = f(g); g = g(x) $$

    $$ \frac{df}{dx} = \frac{df}{dg} \frac{dg}{dx} $$

3. Computational graph

    $$ \hat{y} = x*w $$

    $$ loss = (\hat{y}-y)^2 = (x*w-y)^2 $$

    - Forward pass

        前向传播，定义计算流程

    - Backward propagation

        反向传播，计算导数，更新权重

4. Data and Variable

    Back propagation: $ l.backward() $

    $$ \frac{\partial{loss}}{\partial{w}} = w.grad.data $$

    Weight update (step): $ w.data = w.data - 0.01 * w.grad.data $

    ```python
    import torch
    from torch.autograd import Variable

    x_data = [1.0, 2.0, 3.0]
    y_data = [2.0, 4.0, 6.0]

    w = Variable(torch.Tensor([1.0]),  requires_grad=True)  # Any random value

    # our model forward pass
    def forward(x):
    return x * w

    # Loss function
    def loss(x, y):
    y_pred = forward(x)
    return (y_pred - y) * (y_pred - y)

    # Before training
    print("predict (before training)",  4, forward(4).data[0])

    # Training loop
    for epoch in range(10):
    for x_val, y_val in zip(x_data, y_data):
        l = loss(x_val, y_val)
        l.backward()
        print("\tgrad: ", x_val, y_val, w.grad.data[0])
        w.data = w.data - 0.01 * w.grad.data

        # Manually zero the gradients after updating weights
        w.grad.data.zero_()

    print("progress:", epoch, l.data[0])

    # After training
    print("predict (after training)",  4, forward(4).data[0])
    ```
