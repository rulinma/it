
# 备份和恢复

## 学习指南

### 命令

#### 备份

``` shell
> mysqldump -u root -p123456 word_world verify_code > verify_code.sql
```

#### 恢复

``` shell
> mysql -u root -p123456 word_world  < verify_code.sql
```

### 经验分享

一般结合定时任务执行备份，可以参考crontab。

## 参考资料

1. [mysql 备份数据库中的一张表](https://blog.51cto.com/fuwenchao/1335473)
2. [MySQL数据库增量备份的操作原创](https://cloud.tencent.com/developer/article/2087161)
