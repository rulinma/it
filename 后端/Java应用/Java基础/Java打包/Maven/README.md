# Maven

## 安装

* SDK安装

```shell
    curl -s "https://get.sdkman.io" | bash
    sdk install maven
    mvn -version
```

* Mac的brew安装

* 官方下载安装
  * https://maven.apache.org

## 使用

安装pom文件

``` shell
mvn install:install-file \
    -Dpackaging=pom \
    -Dfile=/Users/rulin/program/gitee/base-parent/pom.xml \
    -DpomFile=/Users/rulin/program/gitee/base-parent/pom.xml
```


## 推荐资料

* [Maven仓库](https://mvnrepository.com) 方便查找库应用。
