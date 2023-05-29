# 常用基础

## 推荐学习

* [2022年你应该知道的Python库](https://zhuanlan.zhihu.com/p/483326822)

## 运行

* 安装Python环境
* pip freeze > requirements.txt
* pip3 install -r requirements.txt
* python3 main.py
  * python main.py
  * python3 run.py

### docker

```text
FROM python:3.9.5-alpine3.12

WORKDIR /app
COPY . .

RUN pip install -r requirements.txt

CMD ["python", "main.py"]
```

* docker build -t my-python-app .
* docker run -p 5005:5005 my-python-app
* http://127.0.0.1:5005/

## 打包

* setuptools
* wheel
