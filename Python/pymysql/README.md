# MySQL

## mysql连接

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
