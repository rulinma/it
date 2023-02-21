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

* docker资源配置要注意，可以把CPU，内存，交换空间等调大点，否则不够容易引起问题

* 搭建自己的docker harbor环境
* 从自由docker harbor推送和获取镜像

### 常用命令

**下面命令也是从项目笔记和shell历史记录中获取，待重新整理。**

* docker
* docker info
* docker ps
  * 查看当前运行容器
  * docker ps -a
    * 查看所有容器，包括停止的
* docker search gitlab
  * 搜索gitlab相关名称镜像
* docker pull gitlab/gitlab-ce
  * 拉取镜像
* docker images
  * 查看镜像
* docker run
  * gitlab示例

  ``` shell
  > docker run -d \
  --hostname gitlab.rulinma.com \
  --name gitlab \
  --restart always \
  -p 8082:443 -p 8083:80 -p 8084:22 \
  -v /etc/localtime:/etc/localtime:ro \
  -v /usr/local/gitlab_data/gitlab/config:/etc/gitlab \
  -v /usr/local/gitlab_data/gitlab/logs:/var/log/gitlab \
  -v /usr/local/gitlab_data/gitlab/data:/var/opt/gitlab \
  gitlab/gitlab-ce
  ```

  * <http://127.0.0.1:8083>
    * 启动稍慢，502报错可以等一会再试
    * root密码说是/etc/gitlab/initial_root_password文件中，我测试登录不正确，然后修改root密码
      * docker exec -it gitlab bash
      * su - git
      * gitlab-rails console -e production
      * user = User.where(id:1).first
      * user.password='admin@123456'
      * user.password_confirmation='admin@123456'
      * user.save!
      * exit
* docker stats gitlab
  * 查看容器统计信息
* docker restart gitlab
  * 重新启动
* docker ps
  * 查看启动容器
* docker container ls -a
* docker logs --help
* docker inspect 6a64d8b3725d
* docker stop 1d65d13b500b
* docker stop gitlab
  * 停止容器
* docker rm container 1d65d13b500b
  * 删除容器
* docker rmi b08de10dc311
  * 删除镜像
  * docker ps -a
    * 检查是否删除
* docker run --name nginx -p 80:80 -v ~/data/nginx/nginx.conf:/etc/nginx/nginx.conf -v ~/data/nginx/www/:/usr/share/nginx/html/ -v ~/data/nginx/logs/:/var/log/nginx/ -v ~/data/nginx/conf/:/etc/nginx/conf.d --privileged=true -d nginx
* docker exec -it nginx /bin/bash
* docker cp 2ccb68715967:/etc/nginx/nginx.conf ~/data/nginx/
* docker pull nginx:1.21.6
* docker rmi -f cb09169b52d4
* docker-machine status

### Dockerfile

Dockerfile_Word

``` text

FROM openjdk:8-jdk
VOLUME /tmp
ARG JAR_FILE=open-word-1.0-SNAPSHOT.jar
COPY ${JAR_FILE} open-word.jar
EXPOSE 8082
ENV JAVA_OPTS=""
ENTRYPOINT java $JAVA_OPTS -Djava.security.egd=file:/dev/./urandom -jar /open-word.jar

```

* docker build -f Dockerfile_Word -t open-word:0.1 --rm=true .

## 参考文献

1. [docker](https://www.docker.com)
2. [docker github](https://github.com/docker)
3. [docker hub](https://hub.docker.com)
4. [Dockerfile reference](https://docs.docker.com/engine/reference/builder)
5. [Dockerfile参考](https://dockerdocs.cn/engine/reference/builder/)
6. [Docker 教程](https://www.runoob.com/docker/docker-tutorial.html)
7. [goharbor](https://goharbor.io)
8. [harbor](https://github.com/goharbor/harbor)
9. [commandline](https://docs.docker.com/engine/reference/commandline/docker)
10. [gitlab-ce](https://hub.docker.com/r/gitlab/gitlab-ce)
