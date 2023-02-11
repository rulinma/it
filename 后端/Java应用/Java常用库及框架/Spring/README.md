# Spring

## 学习指南

### 推荐资料

* [图书]精通Spring
* [图书]Spring in Action
* [图书]Spring Recipes
* 推荐阅读一个[tiny-spring](https://github.com/code4craft/tiny-spring)

### 学习步骤

## 知识点

* mysql驱动需要更新到比较新的版本，驱动类名称也有调整，避免很多莫名的错误

    ``` pom
    
    <mysql-connector.version>8.0.11</mysql-connector.version>
    ```

    ``` yml
    spring:
        datasource:
            driver-class-name: com.mysql.cj.jdbc.Driver
    ```

## 项目实战

## 参考文献
