# 日志

## 学习指南

### 推荐资料

* [Log4j](https://logging.apache.org/log4j/2.x/)
* [SLF4j](https://www.slf4j.org)
* [Logback](https://logback.qos.ch)
* [Common-Logging](http://commons.apache.org/proper/commons-logging)

### 学习步骤

## 知识点

* 不同环境可以配置不同日志文件，方便设置日志等级等
  * spring boot整合logback参考示例
    * bootstrap.yml

    ``` yml
    logging:
        config: classpath:logback-${spring.profiles.active}.xml
    ```

    * 日志配置文件
      * logback.xml
      * logback-dev.xml
      * logback-test.xml
      * logback-pre.xml
      * logback-prod.xml
    * 启动参数
      * -Dspring.profiles.active=dev
        * java -Xms64m -Xmx512m -Dspring.profiles.active=prod -jar word-world-1.0-SNAPSHOT.jar

## 项目实战

## 参考文献
