# 规范

## 马如林的Linux自定义规范

### 马如林的Linxu目录自定义规范

* mkdir /tools/*
  * 存放自己安装的工具目录
    * /tools/nacos
    * /tools/other

* mkdir /app/*
  * 应用程序等存放该目录
    * /app/$project
      * /app/$project/startup
        * 存放该项目的启动程序
      * /app/$project/timer/sh
        * 存放该项目的定时脚本

* mkdir /data/*
  * 数据文件等存放该目录
    * /data/backup/$project/db
    * /data/logs/$project/log
