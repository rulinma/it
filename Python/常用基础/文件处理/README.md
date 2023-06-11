# 文件处理

## PDF处理

``` python
from reportlab.pdfgen.canvas import Canvas
from pdfrw import PdfReader
from pdfrw.toreportlab import makerl
from pdfrw.buildxobj import pagexobj
import pdfrw
from reportlab.pdfbase import pdfmetrics
```

字体处理：复制字体文件到项目文件支持汉字

``` shell
~/.virtualenvs/word-spider/lib/python3.9/site-packages/reportlab/fonts
```
