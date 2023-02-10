# Docker

## 学习指南

* 下载并安装
* 学会使用docker基础命令
* 修改默认镜像仓库地址
* 常用中间件的docker启动
  * Mysql
  * Redis
  * ElasticSearch
* 学会dockfile文件内容
* 自己写的程序放入dockr并对外提供服务

* 搭建自己的docker harbor环境
* 从自由docker harbor推送和获取镜像

### 常用命令

**下面命令也是从项目笔记和shell历史记录中获取，待重新整理。**

* docker
* docker info
* docker ps
* docker container ls -a
* docker logs --help
* docker inspect 6a64d8b3725d
* docker stop 1d65d13b500b
* docker rm container 1d65d13b500b
* docker run --name nginx -p 80:80 -v ~/data/nginx/nginx.conf:/etc/nginx/nginx.conf -v ~/data/nginx/www/:/usr/share/nginx/html/ -v ~/data/nginx/logs/:/var/log/nginx/ -v ~/data/nginx/conf/:/etc/nginx/conf.d --privileged=true -d nginx
* docker exec -it nginx /bin/bash
* docker cp 2ccb68715967:/etc/nginx/nginx.conf ~/data/nginx/
* docker pull nginx:1.21.6
* docker rmi -f cb09169b52d4
* docker-machine status

## 参考文献

1. [docker](https://www.docker.com)
2. [docker github](https://github.com/docker)
3. [docker hub](https://hub.docker.com)
4. [Docker 教程](https://www.runoob.com/docker/docker-tutorial.html)
5. [goharbor](https://goharbor.io)
6. [harbor](https://github.com/goharbor/harbor)
7. [commandline](https://docs.docker.com/engine/reference/commandline/docker)
