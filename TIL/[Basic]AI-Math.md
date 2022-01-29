# Basic
*Basic of basic*
## Vector

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

---------

## Matrix
```python
## 3X3
X = np.array([[1, -2, 3],
             [7, 5, 0],
             [-2, -1, 2]])
```

**Matrix multiplication**
```python
X = np.array([[1, -2, 3],
              [7, 5, 0],
              [-2, -1, 2]])
Y = np.array([[0, 1],
              [1, -1],
              [-2, 1]])

X @ Y
## array([[-8, 6],
##        [ 5, 2],
##        [-5, 1]])
```


**Matrix inner**
```python
X = np.array([[1, -2, 3],
              [7, 5, 0],
              [-2, -1, 2]])
Y = np.array([[0, 1, -1],
              [1, -1, 0]])

np.inner(X, Y)
## array([[-5, 3],
##	[ 5, 2],
##	[-3, -1]])
```

**역행렬**
`np.linalg.inv(X)`

**유사 역행렬 (무어-펜로즈(Moore-Penrose) 역행렬) A+**
행과 열의 개수가 달라도 역행렬 계산 가능


## Softmax
```python
def softmax(vec):
  # 출력값에 대해 지수함수를 씌움
  # 너무 큰 벡터가 들어오면 overflow가 일어날 수 있어서
  # max값은 vec로 빼두고 exp적용
  denumerator = np.exp(vec = np.max(vec, axis=-1, keepdims=True))
  # 모든 denumerator을 더해줌 (분자)
  numerator = np.sum(denumerator, axis=-1, keepdims=True)
  val = denumerator / numerator
  return val
```
