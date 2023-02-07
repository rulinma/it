# MySQL

[MySQL](https://www.mysql.com)

## 学习指南

### MySQL 安装

#### CentOS安装

##### 环境准备

```shell
> wget -i -c http://dev.mysql.com/get/mysql57-community-release-el7-10.noarch.rpm
> yum -y install mysql57-community-release-el7-10.noarch.rpm
> rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2022
> yum -y install mysql-community-server
> systemctl status mysqld
```

##### 修改配置文件（仅供参考）

/etc/my.cnf

```text

[client]
port = 3306
socket = /data/mysql/mysql.sock

[mysqld]
port=3306
socket=/data/mysql/mysql.sock
character-set-server=utf8
collation-server=utf8_general_ci

#数据目录
datadir=/data/mysql/data/
#pid文件
pid-file=/data/mysql/mysql.pid
user=mysql
server_id=1

#二进制日志
log_bin_index=/data/mysql/log/mysql-bin.index
log_bin=/data/mysql/log/mysql-bin
binlog_format=row
#错误日志
log_error=/data/mysql/log/mysql-error.log

#慢查询日志
slow_query_log=1
#long_query_time=1
slow_query_log_file=/data/mysql/log/mysql-slow.log

```

##### MySQL初始化

创建用户组，用户和目录，并授权。

```shell
> groupadd mysql
> useradd -r -g mysql -s /bin/false mysql
> mkdir /data/mysql/data -p
> mkdir /data/mysql/log -p
> chown -R mysql:mysql /data/mysql/
> chmod -R go-rwx /data/mysql/data/
> chmod +t /data/mysql/
```

初始化mysql，并查看状态。

```shell
> mysqld --initialize --user=mysql
> systemctl start mysqld
> systemctl status mysqld
```

查看默认密码。

```shell
> cat /data/mysql/log/mysql-error.log | grep pass
2023-02-03T09:42:02.136334Z 1 [Note] A temporary password is generated for root@localhost: ne/W#r51ed6f
> 
```

本地使用默认密码登录。

```shell
> mysql -p
> 
```

修改root密码并授权哪些机器能够访问。

```sql
mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY 'paws12#s';
mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'183.191.113.214' IDENTIFIED BY 'paws12#s' WITH GRANT OPTION;
mysql> FLUSH PRIVILEGES;
```

### MySQL常用命令

#### 验证命令

```sql
mysql> select version()
mysql> select now()
mysql> select * from mysql.user
```

#### 管理命令

##### 创建管理员用户并授权

```sql
mysql> create user demo identified by 'pwdS22Lv';
mysql> grant all privileges on *.*  to demo@'183.191.113.214' identified by 'pwdS22Lv';
mysql> flush privileges;
mysql> grant all privileges on *.*  to demo@'localhost' identified by 'pwdS22Lv';
mysql> flush privileges;
```

##### 创建数据库

```sql
mysql> CREATE DATABASE `word_world`;
```

##### 创建程序用户（dev, tst, prd) 不同环境，不同用户防止串访

```sql
mysql> create user demo_prd identified by 'p1w2d3Sa';
mysql> grant all privileges on word_world.*  to demo_prd@'171.31.82.195' identified by 'p1w2d3Sa';
mysql> flush privileges;
```

##### 授权管理

```sql
mysql> REVOKE Grant Option ON *.* FROM `demo`@`171.31.82.195`
mysql> GRANT Grant Option ON *.* TO `demo`@`171.31.82.195`
mysql> flush privileges;
```

##### 排查问题常用命令

```sql
mysql> show databases;
mysql> use db;
mysql> show tables;
mysql> show grants;
mysql> select user();
mysql> SHOW FULL PROCESSLIST;

# 查看binlog是否开启
mysql> show variables like 'log_%';

The MySQL process list indicates the operations currently being performed by the set of threads executing within the server.
```

##### 数据快速导入

```shell
> mysql -u root -p 
mysql> use your_db_name;
mysql> source /opt/file.sql;
```

### 学习资料

* [图书][MySQL DBA修炼之道](http://product.dangdang.com/24194120.html)
  * 数据库技术专家撰写，多年数据库领域的经验结晶。实战性强，从架构、调优、运维、开发、测试等多个角度对MySQL管理和维护进行了全方位的归纳和总结，包含大量来自实际生产环境的经典案例。

* [图书][MySQL数据库（高洛峰）](http://study.163.com/course/introduction/247003.htm#/courseDetail)
