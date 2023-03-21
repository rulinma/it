
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

### ChatGPT

写一个mysql备份数据库的脚本，压缩和scp传输。

> cat mysql_backup.sh

``` shell
#!/bin/bash

# 备份文件的保存路径
backup_dir="/path/to/backup"

# MySQL用户名和密码
user="your_username"
password="your_password"

# 要备份的数据库名称
database_name="your_database_name"

# 备份文件的命名格式
backup_name="${database_name}_$(date +%Y%m%d%H%M%S).sql"

# 备份文件压缩后的命名格式
compressed_backup_name="${backup_name}.gz"

# 执行备份命令
mysqldump -u $user -p$password $database_name | gzip > $backup_dir/$compressed_backup_name

# 将备份文件通过scp传输到远程服务器
remote_username="your_remote_username"
remote_hostname="your_remote_hostname"
remote_directory="/path/to/remote/backup"

scp $backup_dir/$compressed_backup_name $remote_username@$remote_hostname:$remote_directory
```

请将上述脚本保存为一个文本文件，例如mysql_backup.sh，并将以下变量替换为实际值：

* backup_dir：备份文件的保存路径，确保该目录存在并且具有适当的写入权限。
* user：MySQL用户名。
* password：MySQL用户的密码。
* database_name：要备份的数据库名称。
* remote_username：远程服务器的用户名。
* remote_hostname：远程服务器的主机名或IP地址。
* remote_directory：远程服务器上用于存储备份文件的目录。

运行脚本后，它将使用mysqldump命令将指定数据库的内容备份到指定的文件中，并使用gzip压缩备份文件。备份文件的命名格式为database_name_YYYYMMDDHHMMSS.sql.gz，其中YYYYMMDDHHMMSS为当前时间的年份、月份、日期、小时、分钟和秒。然后，脚本使用scp命令将压缩的备份文件传输到远程服务器的指定目录中。

### 经验分享

一般结合定时任务执行备份，可以参考crontab。

## 参考资料

1. [mysql 备份数据库中的一张表](https://blog.51cto.com/fuwenchao/1335473)
2. [MySQL数据库增量备份的操作原创](https://cloud.tencent.com/developer/article/2087161)
