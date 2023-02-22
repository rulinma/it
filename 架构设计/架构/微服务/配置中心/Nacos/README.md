# Nacos

## 学习指南

### Nacos安装

``` shell

> wget https://github.com/alibaba/nacos/releases/download/1.3.2/nacos-server-1.3.2.zip
> wget -c https://github.com/alibaba/nacos/releases/download/1.3.2/nacos-server-1.3.2.zip

> unzip nacos-server-1.3.2.zip
> cd nacos
> sh bin/startup.sh -m standalone
> sh bin/shutdown.sh

```

* 调整startup.sh的standalone的JVM启动参数，够用就行
  * JAVA_OPT="${JAVA_OPT} -Xms64m -Xmx256m"

* 前端访问
  * http://localhost:8848/nacos/
  * 用户密码: nacos/nacos

## 参考文献

1. [Nacos官网](https://nacos.io/)
2. [Nacos Github](https://github.com/alibaba/nacos)
