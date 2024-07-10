# TensorFlow

## 基础使用

$ conda install tensorflow

https://www.tensorflow.org/install?hl=zh-cn

### TensorBoard

TensorFlow's Visualization Toolkit. TensorBoard is a suite of web applications for inspecting and understanding your TensorFlow runs and graphs.

* tensorboard --logdir=base/logs --port=6006 

``` python
from torch.utils.tensorboard import SummaryWriter

writer = SummaryWriter('base/logs')

for i in range(100):
    writer.add_scalar('y=x', 10*i, i)

writer.close()
``` 

* tensorboard --logdir=base/logs --port=6006    