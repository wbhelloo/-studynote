## ML/DL for Everyone with PyTorch

## Lecture-6_Logistic-Regression

- Sigmoid()

    `torch.nn.functional.sigmoid(input)`

- (Binary) Cross Entropy Loss 

    $$ loss = -\frac{1}{N} \sum_{n=1}^N y_n log \hat{y}_n + (1-y_n)log(1-\hat{y}_n) $$

    `torch.nn.torch.nn.BCELoss`

- 实现代码:

```python
# 导入必要的包
import torch
from torch.autograd import Variable
import torch.nn.functional as F

# 数据集
x_data = Variable(torch.Tensor([[1.0], [2.0], [3.0], [4.0]]))
y_data = Variable(torch.Tensor([[0.], [0.], [1.], [1.]]))
# print('x_data.shape:',x_data.shape)
# print('y_data.shape:',y_data.shape)

########################################################################
class Model(torch.nn.Module):

    def __init__(self):
        """
        In the constructor we instantiate nn.Linear module
        """
        super(Model, self).__init__()
        self.linear = torch.nn.Linear(1, 1)  # One in and one out

    def forward(self, x):
        """
        In the forward function we accept a Variable of input data and we must return
        a Variable of output data.
        """
        y_pred = F.sigmoid(self.linear(x))
        return y_pred

# our model
model = Model()

########################################################################
# Construct our loss function and an Optimizer. The call to model.parameters()
# in the SGD constructor will contain the learnable parameters of the two
# nn.Linear modules which are members of the model.
criterion = torch.nn.BCELoss(size_average=True)
optimizer = torch.optim.SGD(model.parameters(), lr=0.01)

########################################################################
# Training loop
for epoch in range(1000):
    # Forward pass: Compute predicted y by passing x to the model
    y_pred = model(x_data)

    # Compute and print loss
    loss = criterion(y_pred, y_data)
#     print(epoch, loss.data[0])
    print(epoch, loss.data.item())

    # Zero gradients, perform a backward pass, and update the weights.
    optimizer.zero_grad()
    loss.backward()
    optimizer.step()
    
# After training
hour_var = Variable(torch.Tensor([[1.0]]))
print("predict 1 hour ", 1.0, model(hour_var).data[0][0] > 0.5)
hour_var = Variable(torch.Tensor([[7.0]]))
print("predict 7 hours", 7.0, model(hour_var).data[0][0] > 0.5)  
```