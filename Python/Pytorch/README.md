# Pytorch

[pytorch](https://pytorch.org)

PyTorch is a Python package that provides two high-level features:

Tensor computation (like NumPy) with strong GPU acceleration
Deep neural networks built on a tape-based autograd system
You can reuse your favorite Python packages such as NumPy, SciPy, and Cython to extend PyTorch when needed.

Tensors and Dynamic neural networks in Python with strong GPU acceleration.


## 安装

* Anaconda
  * conda install pytorch torchvision -c pytorch
* pip
  * pip3 install torch torchvision

验证

``` python
import torch
x = torch.rand(5, 3)
print(x)
```
