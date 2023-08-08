# Neo4j

## 学习指南

* [Neo4j](https://neo4j.com/) The graph database platform.(图数据库平台)

* 快速启动

    ``` shell
    docker run \
        --name testneo4j \
        -p7474:7474 -p7687:7687 \
        -d \
        -v $HOME/neo4j/data:/data \
        -v $HOME/neo4j/logs:/logs \
        -v $HOME/neo4j/import:/var/lib/neo4j/import \
        -v $HOME/neo4j/plugins:/plugins \
        --env NEO4J_AUTH=neo4j/password \
        neo4j:latest
    ```

    <http://localhost:7474/browser/>

    You are connected as user neo4j
    to neo4j://localhost:7687

## 基础知识

Cypher

``` text
    Cypher was inspired by an ASCII-art type of syntax where (nodes)-[:ARE_CONNECTED_TO]->(otherNodes) using rounded brackets for circular (nodes), and -[:ARROWS]-> for relationships. When you write a query, you draw a graph pattern through your data.
```

Node

``` text
    ()                  //anonymous node (no label or variable) can refer to any node in the database
    (p:Person)          //using variable p and label Person
    (:Technology)       //no variable, label Technology
    (work:Company)      //using variable work and label Company
pattern through your data.
```

Relation

``` text
    //data stored with this direction
    CREATE (p:Person)-[:LIKES]->(t:Technology)

    //query relationship backwards will not return results
    MATCH (p:Person)<-[:LIKES]-(t:Technology)

    //better to query with undirected relationship unless sure of direction
    MATCH (p:Person)-[:LIKES]-(t:Technology)
```

## 自己建立关系和CRUD等操作

- 创建、更新、删除节点和关系 - 通过模式匹配来查询和修改节点和关系 - 管理索引和约束等

1. 删除所有
    MATCH (n) DETACH DELETE n
2. 创建节点
	CREATE (:Person {name: 'John'})
	CREATE (:Person {name: 'Mary'})

	CREATE (n:Person {name:'John'}) RETURN n
	CREATE是创建操作，Person是标签，代表节点的类型。花括号{}代表节点的属性，属性类似Python的字典。这条语句的含义就是创建一个标签为Person的节点，该节点具有一个name属性，属性值是John。

3. 创建关系
	MATCH (a:Person), (b:Person)
	WHERE a.name = 'John' AND b.name = 'Mary'
	CREATE (a)-[:KNOWS]->(b)

	KNOWS位关系的类型，就是KNOWS的关系。

	MATCH (a:Person {name:'Shawn'}),
      (b:Person {name:'Sally'})
	MERGE (a)-[:FRIENDS {since:2001}]->(b)
	在关系中，同样的使用花括号{}来增加关系的属性，也是类似Python的字典，这里给FRIENDS关系增加了since属性，属性值为2001，表示他们建立朋友关系的时间。

4. 查询节点
	MATCH (n) RETURN n
5. 组合查询
	MATCH (a:Person)-[r:KNOWS]->(b:Person)
	RETURN a, r, b

### 常用功能

两节点之间的所有路径
两节点之间直接连接
查询两节点之间最短路径
查询两节点之间所有的最短路径
查询多层关系

## 参考文献

1. <https://zhuanlan.zhihu.com/p/88745411>
2. <https://neo4j.com/docs/getting-started/cypher-intro/>
3. <https://blog.csdn.net/u011250186/article/details/107234087>
4. <https://blog.csdn.net/wavehaha/article/details/111592161>
