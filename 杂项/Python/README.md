# Python

* 脚本语言

## 学习指南

* python2 和 python3有区别

* 主要应用领域
  * 运维
  * 爬虫
  * 人工智能
  * 自动化测试

* 基础学习后根据实际情况选择学习路线，不要都学

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

db = pymysql.connect(host="127.0.0.1",user="root",password="123456",database="my_test")

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

### 推荐资料

* [图书][Python基础教程](http://product.dangdang.com/25218035.html)
* [图书]Python核心编程

## 参考资料

1. [廖雪峰的Python教程](https://www.liaoxuefeng.com/wiki/1016959663602400)
2. [Python3 MySQL 数据库连接 - PyMySQL 驱动](https://www.runoob.com/python3/python3-mysql.html)
3. [Python - 100天从新手到大师](https://github.com/jackfrued/Python-100-Days)
4. [官方Python 教程](https://docs.python.org/zh-cn/3/tutorial/index.html)
5. [W3School Python 教程](https://www.w3school.com.cn/python/index.asp)
