# TensorFlow

## 基础使用

* tensorboard --logdir=base/logs --port=6006 

``` python
from torch.utils.tensorboard import SummaryWriter

writer = SummaryWriter('base/logs')

for i in range(100):
    writer.add_scalar('y=x', 10*i, i)

writer.close()
``` 

* tensorboard --logdir=base/logs --port=6006    