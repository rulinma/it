<!--
 * @Author: rulinma rulinma@gmail.com
 * @Date: 2023-02-17 10:52:49
 * @LastEditors: rulinma rulinma@gmail.com
 * @LastEditTime: 2023-03-03 12:31:58
 * @Description: 程序员学习和实战指南 https://github.com/rulinma/it 获取更多内容
 * @copyright: 马如林保留所有版权
-->
# IntelliJ

## 学习指南

### 推荐资料

* [Findbugs](http://findbugs.sourceforge.net) 一般用在IDE插件，帮助发现bug。(This is the web page for FindBugs, a program which uses static analysis to look for bugs in Java code. )
* [Checkstyle](https://checkstyle.org) Checkstyle is a development tool to help programmers write Java code that adheres to a coding standard. By default it supports the Google Java Style Guide and Sun Code Conventions, but is highly configurable. It can be invoked with an ANT task and a command line program.(Checkstyle是一种开发工具，可帮助程序员编写符合编码标准的Java代码。 默认情况下，它支持Google Java样式指南和Sun代码约定，但具有高度可配置性。 它可以使用ANT任务和命令行程序调用)
  * [Checkstyle](https://github.com/checkstyle/checkstyle)

## Q&A

* IDEA打开后一直响，操作难以维持，特别是打开多个窗口的情况。
  * 修改IDEA安装目录下的idea.vmoptions文件内容，默认比较小，改大点。

    ``` text
    -Xms1024m
    -Xmx3072m
    -XX:ReservedCodeCacheSize=512m
    -XX:+UseCompressedOops
    ```
