# ML/DL for Everyone with PyTorch

## Lecture-5_Linear-regression-in-PyTorch-way

### PyTorch Rhythm 

- Design your model using class with Variables

- Construct loss and optimizer(select from PyTorch API)

- Training cycle (forward, backward, update)

```python
import torch
from torch.autograd import Variable

# Data definition (3x1)

x_data = Variable(torch.Tensor([[1.0], [2.0], [3.0]]))
y_data = Variable(torch.Tensor([[2.0], [4.0], [6.0]]))


########################################################################
# 1.Design your model using class with Variables

class Model(torch.nn.Module):
    def __init__(self):
        """
        In the constructor we instantiate two nn.Linear module
        """
        super(Model, self).__init__()
        self.linear = torch.nn.Linear(1, 1)  # One in and one out

    def forward(self, x):
        """
        In the forward function we accept a Variable of input data and we must return
        a Variable of output data. We can use Modules defined in the constructor as
        well as arbitrary operators on Variables.
        """
        y_pred = self.linear(x)
        return y_pred

# our model
model = Model()


########################################################################
# 2.Construct loss and optimizer (select from PyTorch API)

# Construct our loss function and an Optimizer. The call to model.parameters()
# in the SGD constructor will contain the learnable parameters of the two
# nn.Linear modules which are members of the model.

criterion = torch.nn.MSELoss(size_average=False)
optimizer = torch.optim.SGD(model.parameters(), lr=0.01)


########################################################################
# 3. Training: forward, loss, backward, step

# Training loop
for epoch in range(100):
    # Forward pass: Compute predicted y by passing x to the model
    y_pred = model(x_data)

    # Compute and print loss
    loss = criterion(y_pred, y_data)
    # print("epoch:", epoch + 1, " loss:", loss.data[0])
    print("epoch:", epoch+1, " loss:%.3f" % loss.data.item())

    # Zero gradients, perform a backward pass, and update the weights.
    optimizer.zero_grad()
    loss.backward()
    optimizer.step()

# After training
hour_var = Variable(torch.Tensor([[4.0]]))
y_pred = model(hour_var)
print("predict (after training)",  4, model(hour_var).data[0][0])
```
