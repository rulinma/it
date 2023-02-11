# 关系数据库

## 学习指南

### 推荐资料

* [图书][经典]Transact-SQL权威指南
* [图书][Architecture of a Database System(数据库系统架构)](http://product.dangdang.com/1058752208.html)
* [图书][Head First SQL](http://product.dangdang.com/21040398.html)

* [图书][经典][Teach Yourself SQL in 21 Days](http://product.dangdang.com/1244621523.html)
* [图书][SQL必知必会(第3版)](http://product.dangdang.com/23246707.html)
* [图书][SQL教程（杨中科）](http://study.163.com/course/introduction/215012.htm#/courseDetail) 使用微软SQL Server讲解的。

### 学习步骤

## 知识点

### Codd 12 Rules

* 默认repeatable-read可重复读
  * read-uncommitted(读取未提交)： 最低的隔离级别，允许读取尚未提交的数据变更，可能会导致脏读、幻读或不可重复读。
  * read-committed(读取已提交)： 允许读取并发事务已经提交的数据，可以阻止脏读，但是幻读或不可重复读仍有可能发生。
  * repeatable-read(可重复读)： 对同一字段的多次读取结果都是一致的，除非数据是被本身事务自己所修改，可以阻止脏读和不可重复读，但幻读仍有可能发生。
  * serializable(可串行化)： 最高的隔离级别，完全服从ACID的隔离级别。所有的事务依次逐个执行，这样事务之间就完全不可能产生干扰，也就是说，该级别可以防止脏读、不可重复读以及幻读。

### CAP理论: 又称CAP定理，指的是在一个分布式系统中， Consistency（一致性）、 Availability（可用性）、Partition tolerance（分区容错性），三者不可得兼

* 理论首先把分布式系统中的三个特性进行了如下归纳：
  * 一致性（C）：在分布式系统中的所有数据备份，在同一时刻是否同样的值。（等同于所有节点访问同一份最新的数据副本）
  * 可用性（A）：在集群中一部分节点故障后，集群整体是否还能响应客户端的读写请求。（对数据更新具备高可用性）
  * 分区容错性（P）：以实际效果而言，分区相当于对通信的时限要求。系统如果不能在时限内达成数据一致性，就意味着发生了分区的情况，必须就当前操作在C和A之间做出选择。

### 影子表

影子表指的是一张真实表“背后”创建的表。当完成建表操作后，可以通过一个原子的重命名操作切换影子表和原表。

``` sql
drop table if exists user_new, user_old;
create table user_new like user;
rename table user to user_old, user_new to user;
```

## 项目实战

## 参考文献
