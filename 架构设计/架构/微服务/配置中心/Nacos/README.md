<!--
 * @Author: rulinma rulinma@gmail.com
 * @Date: 2023-02-17 10:52:49
 * @LastEditors: rulinma rulinma@gmail.com
 * @LastEditTime: 2023-03-04 10:08:04
 * @Description: 程序员学习和实战指南 https://github.com/rulinma/it 获取更多内容
 * @copyright: 马如林保留所有版权
-->
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
  * <http://localhost:8848/nacos/>
  * 用户密码: nacos/nacos

### 开机自动重启

* 编写配置文件
  * vim  /etc/systemd/system/nacos.service

    ``` text
    [Unit]
    Description=nacos
    After=network.target

    [Service]
    Type=forking
    ExecStart=/tools/nacos/bin/startup.sh -m standalone
    ExecReload=/tools/nacos/bin/shutdown.sh
    ExecStop=/tools/nacos/bin/shutdown.sh
    Restart=always
    RestartSec=2
    PrivateTmp=true 

    [Install] 
    WantedBy=multi-user.target
    ```

* systemctl daemon-reload
  * 重载所有服务
* systemctl enable nacos
  * 设置开机自启动
* systemctl is-enabled nacos
  * 查看开机启动状态
* systemctl status nacos
  * 查看服务状态
* systemctl start nacos
  * 启动 Nacos
* systemctl stop nacos
  * 停止 Nacos
* systemctl restart nacos
  * 重启 Nacos

## 参考文献

1. [Nacos官网](https://nacos.io/)
2. [Nacos Github](https://github.com/alibaba/nacos)
3. [Linux下设置Java项目开机自启动](https://www.cnblogs.com/wiliamzhao/p/16502166.html)
