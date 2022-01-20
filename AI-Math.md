## Basic
**Vector**

```python
import numpy as np

x = np.array([1, 7, 2])
y = np.array([5, 2, 1])

x + y
## array([6, 9, 3])

x - y
## array([-4, 5, 1])

x * y
## array([5, 14, 2])
```


**Norm**
```python
def l1_norm(x):
  x_norm = np.abs(x)
  x_norm = np.sum(x_norm)
  return x_norm

def l2_norm(x): ## np.linalg.norm
  x_norm = x*x
  x_norm = np.sum(x_norm)
  x_norm = np.sqrt(x_norm)
  return x_norm
```


**Angle**
```python
def angle(x, y):
	v = np.inner(x, y) / (l2_norm(x) * l2_norm(y))
  theta = np.arccos(v)
  return theta
```

**Matrix**
```python
## 3X3
X = np.array([[1, -2, 3],
             [7, 5, 0],
             [-2, -1, 2]])
```
