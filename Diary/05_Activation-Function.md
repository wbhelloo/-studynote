### 阶跃函数

```python
import numpy as np
import matplotlib.pylab as plt

def step_function(x):
    return np.array(x>0, dtype=np.int)

# 预览阶跃函数图形
x = np.arange(-5.0, 5.0, 0.1)
y = step_function(x)
plt.plot(x,y)
plt.ylim(-0.1, 1.1)
plt.title('Step')
plt.show()
```

### Sigmoid函数

```python
import numpy as np
import matplotlib.pylab as plt

def sigmoid(x):
    return 1/(1 + np.exp(-x))

# 预览Sigmoid函数图形
x = np.arange(-5.0, 5.0, 0.1)   # Numpy数组
y = sigmoid(x)
plt.plot(x,y)
plt.ylim(-0.1, 1.1)
plt.title('Sigmoid')
plt.show()
```

### Relu函数

```python
import numpy as np
import matplotlib.pylab as plt

def relu(x):
    return np.maximum(0, x)

x = np.arange(-5.0, 5.0, 0.1)   # Numpy数组
y = relu(x)
plt.plot(x,y)
plt.ylim(-1, 6)
plt.title('Relu')
plt.show()
```
