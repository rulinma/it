# 定时任务

## 定时工具

### Crontab

[Linux crontab 命令](https://www.runoob.com/linux/linux-comm-crontab.html)

* shell命令

``` shell
> crontab -l
> crontab -e
```

* 参数说明

``` text

0    2    *    *    6
*    *    *    *    *    *
-    -    -    -    -    -
|    |    |    |    |    |
|    |    |    |    |    + 年 [可选参数]
|    |    |    |    +----- 星期几 (0 - 7) (Sunday=0 or 7)
|    |    |    +---------- 月份 (1 - 12)
|    |    +--------------- 几号 (1 - 31)
|    +-------------------- 小时 (0 - 23)
+------------------------- 分钟 (0 - 59)
```

* [在线crontab表达式验证工具](https://www.oren.net.cn/tool/cron.html)
* [crontab执行时间计算](https://tool.lu/crontab/)

#### crontab示例

``` text
# 每天3点执行备份表操作

0 3 * * * /app/xianglesong/timer/sh/mysql_backup_table.sh > /data/backup/xianglesong/db/mysql_backup_table.log 2>&1

```

``` shell
> cat mysql_backup_table.sh 
mysqldump -u root -p123456 word_world comments > /data/backup/xianglesong/db/comments.sql
mysqldump -u root -p123456 word_world comments_action > /data/backup/xianglesong/db/comments_action.sql
mysqldump -u root -p123456 word_world user_basic > /data/backup/xianglesong/db/user_basic.sql
```
