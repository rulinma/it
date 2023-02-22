# Redis

## 学习指南

### 安装Redis

#### yum安装

  ``` shell

  > yum install epel-release
  > yum update
  > yum -y install redis
  > systemctl start redis
  > systemctl status redis
  # 移除命令
  # > yum remove redis
  ```

#### yum安装新版本(7.X)

  ``` shell
  > yum install -y http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
  > yum --enablerepo=remi install redis
  > systemctl start redis
  > rpm -qa |grep redis
  > redis-cli --version
  > systemctl enable redis.service
  ```

* 修改配置文件

  ``` shell

  > cat /etc/redis.conf
    bind 0.0.0.0
    daemonize yes
    protected-mode no
    ...

  ```

#### 源码安装

#### 配置文件redis.conf修改

```text
bind 0.0.0.0
daemonize yes
protected-mode no
```

#### 启动Redis和测试

```shell
# 启动redis server
> /usr/local/bin/redis-server /etc/redis.conf
> redis-cli -p 6379
> redis-cli -p 6379 shutdown
> netstat -tlnp
```

##### 密码访问

```shell
> redis-cli -h 127.0.0.1 -p 6379 -a foobar
```

#### 开机重启

#### 自动重启

### 常用命令

### 推荐资料

* [工具][Redis Desktop Manager](https://redisdesktop.com/)  
  * 访问Redis的工具。(Redis Desktop Manager (aka RDM) — is a fast open source Redis database management application for Windows, Linux and MacOS.)

* [图书][Redis实战](http://product.dangdang.com/23800641.html)
