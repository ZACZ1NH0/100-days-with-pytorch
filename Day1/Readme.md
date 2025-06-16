# 🧠 100 Days with PyTorch – Day 1: Tensor Basics

Welcome to Day 1 of the **100 Days with PyTorch** journey!  
Today we explore the fundamentals of **tensors** – the core data structure of PyTorch.

---

## 🔥 What I Learned

✅ How to create tensors  
✅ Tensor data types and shapes  
✅ Basic tensor operations: addition, subtraction, multiplication, division  
✅ Conversion between NumPy arrays and PyTorch tensors  
✅ Broadcasting and `alpha` parameter in `torch.add`  
✅ Handling shape and equality
---

## 📌 Key Code Examples

```python
import torch
import numpy as np

# Create tensors
a = torch.tensor([1, 2, 3])
b = torch.tensor([4, 5, 6])

# Addition with alpha
c = torch.add(a, b, alpha=2)  # a + 2*b

# Subtraction
d = a - b

# Element-wise multiplication
e = a * b

# Element-wise division
f = a / b

# Integer division with rounding
g = torch.div(a, b, rounding_mode='trunc')

# Convert NumPy to Tensor
data = [[1, 2, 3], [4, 5, 6]]
np_data = np.array(data)
y = torch.from_numpy(np_data)

# Tensor equality check
x = torch.tensor(data)
print(torch.equal(x, y))  # True if dtype, shape, and device match
