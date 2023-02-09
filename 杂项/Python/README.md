# Python

* 脚本语言

## 学习指南

* python2 和 python3有区别
* 瑞士军刀性的工具

### mysql连接

python访问mysql的示例：

``` shell
> cat mysql.py
```

``` python
#!/usr/bin/python3

import pymysql

__author__ = 'rulinma'

import pymysql

db = pymysql.connect(host="127.0.0.1",user="root",password="123456",database="rulin_test")

cursor = db.cursor()

sql = "SELECT * FROM dict"
try:
   cursor.execute(sql)
   results = cursor.fetchall()
   for row in results:
      id = row[0]
      deleted = row[1]
      print ("id=%s,deleted=%s" % \
             (id, deleted))
except:
   print ("Error: unable to fetch data")

db.close()


```

``` shell
> python3 mysql.py
id=1,deleted=1
id=2,deleted=0
id=3,deleted=1
```

### 核心资料

* [图书][Python基础教程](http://product.dangdang.com/25218035.html)
* [图书]Python核心编程

## 参考资料

1. [Python3 MySQL 数据库连接 - PyMySQL 驱动](https://www.runoob.com/python3/python3-mysql.html)