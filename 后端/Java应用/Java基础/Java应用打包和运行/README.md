# Java打包和运行

## 学习指南

### 知识点

#### 启动程序常用命令及说明

* java -jar test.jar
  * 运行 jar 包，在命令行输出内容，关闭命令行则程序退出，可以用 ctrl+C 主动退出
* java -jar test.jar &
  * 使用 & 代表后台运行 jar 包，不影响当前命令行的继续使用，关闭命令行时退出程序
* nohup java -jar test.jar &
  * 使用 nohup 表示不挂断运行命令，即程序可以后台运行，不影响命令行继续使用，且关闭命令行后程序不停止；nohup 不指定输出文件时，默认将命令行输出重定向到 nohup.out 文件
* nohup java -jar test.jar > /dev/null 2>&1 &
  * 输出内容到空设备
* nohup java -server -Xms64m -Xmx512m -Dspring.profiles.active=dev -jar test.jar "$@" > /dev/null 2>&1 &
  * 设置JVM参数及自定义参数和传递程序启动参数

#### 产线常用JVM调优参数

* 垃圾回收算法
* dump文件地址
* 内存配比
* 垃圾回收日志
* 不同应用需求配置也会不同

* 日活超百万的一个配置（线上检验过的，压力测试过的）
  
  ``` text
  command=java -server -Xms8192M -Xmx8192M -Xmn2g -Xss256k -XX:+HeapDumpOnOutOfMemoryError -XX:MetaspaceSize=256m -XX:MaxMetaspaceSize=256m -XX:+DisableExplicitGC -XX:SurvivorRatio=1 -XX:LargePageSizeInBytes=128M -XX:+UseFastAccessorMethods -XX:SoftRefLRUPolicyMSPerMB=0 -XX:+ScavengeBeforeFullGC -XX:+UseG1GC -XX:MaxGCPauseMillis=200 -XX:InitiatingHeapOccupancyPercent=45 -XX:+PrintClassHistogram -XX:+PrintGCDetails -XX:+PrintGCTimeStamps -XX:+PrintHeapAtGC -Xloggc:/data/logs/app/gc.log -jar -DDEPLOY_ENV=prd /data/web/word-backend/current/word-backend-1.0.0-SNAPSHOT.jar
  ```

* Elasticsearch的参考配置

  ``` text
  command=java -Xms8g -Xmx8g -Djava.awt.headless=true -XX:+UseParNewGC -XX:+UseConcMarkSweepGC -XX:CMSInitiatingOccupancyFraction=75 -XX:+UseCMSInitiatingOccupancyOnly -XX:+HeapDumpOnOutOfMemoryError -XX:+DisableExplicitGC -Dfile.encoding=UTF-8 -Delasticsearch -Des.pidfile=/var/run/elasticsearch/elasticsearch.pid -Des.path.home=/usr/share/elasticsearch -cp :/usr/share/elasticsearch/lib/elasticsearch-1.7.4.jar:/usr/share/elasticsearch/lib/*:/usr/share/elasticsearch/lib/sigar/* -Des.default.path.home=/usr/share/elasticsearch -Des.default.path.logs=/var/log/elasticsearch -Des.default.path.data=/var/lib/elasticsearch -Des.default.path.work=/tmp/elasticsearch -Des.default.path.conf=/etc/elasticsearch org.elasticsearch.bootstrap.Elasticsearch
  ```
