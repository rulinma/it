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

Node or relationship properties

```
    Node property: (p:Person {name: 'Sally'})

    Relationship property: -[rel:IS_FRIENDS_WITH {since: 2018}]->
```

Patterns in Cypher

```
    (p:Person {name: "Sally"})-[rel:LIKES]->(g:Technology {type: "Graphs"})
```

### 数据模型

```
Nodes (circles) represent objects.

Nodes can have properties (name/value pairs).

Relationships (arrows) connect nodes and represent actions.

Relationships are directional and can have properties (name/value pairs).

Labels: A label is a named graph construct that is used to group nodes into sets. All nodes labeled with the same label belongs to the same set.

```

```
    MERGE (j:Person {name: 'John'})
    ON CREATE set j.age = 27
    MERGE (s:Person {name: 'Sally'})
    ON CREATE set s.age = 32
    MERGE (b:Book {title: 'Graph Databases'})
    ON CREATE set b.authors = ['Jim Webber', 'Ian Robinson']
    MERGE (j)-[rel1:IS_FRIENDS_WITH]->(s)
    ON CREATE SET rel1.since = '01/09/2013'
    MERGE (j)-[rel2:HAS_READ]->(b)
    ON CREATE SET rel2.on = '02/03/2013', rel2.rated = 5
    MERGE (s)-[rel3:HAS_READ]->(b)
    ON CREATE SET rel3.on = '02/09/2013', rel3.rated = 4
```

```
    MATCH (n) RETURN n
```

## 基本操作演示

### 常用命令

:help cypher

1. 删除所有
	MATCH (n) DETACH DELETE n

2. 查询所有
	MATCH (n) RETURN n

3. 添加节点
	CREATE (:Word {word: 'hello', rank: 2252, star: 4})
		具体来看:
		1. CREATE - 表示要创建新实体。
		2. (:Word) - 指定要创建的节点的标签(label)为 Word。
		3. {word: 'hello', rank: 1, star: 5} - 为新节点指定属性及值。这里设置了三个属性:
		    - word - 字符串属性,值为'hello'
		    - rank - 整数属性,值为1
		    - star - 整数属性,值为5
		4. 所以这条语句总结起来就是:
		    创建一个标签为 Word 的新节点,并设置属性 word 为 'hello',rank 为 1,star 为 5。

	CREATE (:Word {word: 'the', rank: 1, star: 5})
	CREATE (:Word {word: 'be', rank: 2, star: 5})
	CREATE (:Word {word: 'they', rank: 22, star: 5})
	CREATE (:Word {word: 'them', rank: 59, star: 5})

   添加唯一约束： CREATE CONSTRAINT FOR (w:Word) REQUIRE w.word IS UNIQUE

	CREATE (:Word {word: 'themselves', rank: 449, star: 5})
	CREATE (:Word {word: 'theme', rank: 1661, star: 3})
	CREATE (:Word {word: 'mathematics', rank: 4293, star: 2})
	CREATE (:Word {word: 'mathematical', rank: 6605, star: 2})
	CREATE (:Word {word: 'anthem', rank: 9702, star: 1})

4. 添加关系

	MATCH (w1:Word {word:'the'}), (w2:Word {word:'they'})
	CREATE (w1)-[:IS_CONTAINED_IN]->(w2)

	MATCH (w1:Word {word:'they'}), (w2:Word {word:'the'})
	CREATE (w1)-[:CONTAINS]->(w2)

	MATCH (w1:Word {word:'the'}), (w2:Word {word:'them'})
	CREATE (w1)-[:IS_CONTAINED_IN]->(w2)

	MATCH (w1:Word {word:'them'}), (w2:Word {word:'the'})
	CREATE (w1)-[:CONTAINS]->(w2)

	MATCH (w1:Word {word:'they'}), (w2:Word {word:'them'})
	CREATE (w1)-[:SIMILAR]->(w2)

	MATCH (w1:Word {word:'themselves'}), (w2:Word {word:'the'})
	CREATE (w1)-[:CONTAINS]->(w2)

	MATCH (w1:Word {word:'theme'}), (w2:Word {word:'the'})
	CREATE (w1)-[:IS_CONTAINED_IN]->(w2)

	MATCH (w1:Word {word:'themselves'}), (w2:Word {word:'them'})
	CREATE (w1)-[:CONTAINS]->(w2)

	MATCH (w1:Word {word:'theme'}), (w2:Word {word:'them'})
	CREATE (w1)-[:CONTAINS]->(w2)

	MATCH (w1:Word {word:'them'}), (w2:Word {word:'theme'})
	CREATE (w1)-[:IS_CONTAINED_IN]->(w2)

5. 查询

* 查询2个词汇是否被包含的关系

	MATCH (n1:Word), (n2:Word)
	WHERE n1.word = 'them' AND n2.word = 'theme'
	RETURN EXISTS((n1)-[:IS_CONTAINED_IN]->(n2)) AS connected

	MATCH (n1:Word), (n2:Word)
	WHERE n1.word = 'the' AND n2.word = 'theme'
	RETURN EXISTS((n1)-[:IS_CONTAINED_IN]->(n2)) AS connected

* 查询2个单词是否相通

	MATCH (w1:Word)-[r]-(w2:Word)
	WHERE w1.word = 'the' AND w2.word = 'theme'
	RETURN TYPE(r) AS rel

* 查询2个单词最短路径

	MATCH p = shortestPath((w1:Word)-[*]-(w2:Word))
	WHERE w1.word = 'the' AND w2.word = 'theme'
	RETURN p

	MATCH p = shortestPath((w1:Word)-[*]-(w2:Word))
	WHERE w1.word = 'the' AND w2.word = 'themselves'
	RETURN p

	MATCH p = shortestPath((w1:Word)-[*]-(w2:Word))
	WHERE w1.word = 'they' AND w2.word = 'themselves'
	RETURN p

	MATCH p = shortestPath((w1:Word)-[*]-(w2:Word))
	WHERE w1.word = 'they' AND w2.word = 'themselves'
	RETURN p

	MATCH p = shortestPath((w1:Word)-[*..3]-(w2:Word))
	WHERE w1.word = 'they' AND w2.word = 'themselves'
	RETURN p

	MATCH p = shortestPath((w1:Word)-[*..2]-(w2:Word))
	WHERE w1.word = 'they' AND w2.word = 'themselves'
	RETURN p

	MATCH p = shortestPath((w1:Word)-[:IS_CONTAINED_IN*]-(w2:Word))
	WHERE w1.word = 'the' AND w2.word = 'theme'
	RETURN p

	MATCH p = shortestPath((w1:Word)-[:CONTAINS|SIMILAR*]-(w2:Word))
	WHERE w1.word = 'they' AND w2.word = 'themselves'
	RETURN p

	MATCH p = shortestPath((w1:Word)-[:CONTAINS|SIMILAR*]-(w2:Word))
	WHERE w1.word = 'they' AND w2.word = 'themselves'
	RETURN p
	ORDER BY LENGTH(p) DESC
	LIMIT 3

	MATCH p = shortestPath((w1)-[:REL1|REL2|REL3*]-(w2))
	MATCH p = shortestPath((w1)-[:REL1|REL2*]-[:REL3]-(w2))

* 查询2个单词所有路径

	MATCH p = ALL((w1:Word)-[:CONTAINS|SIMILAR*]-(w2:Word))
	WHERE w1.word = 'they' AND w2.word = 'themselves'
	RETURN p

	MATCH p = ALL((w1:Word)-[:CONTAINS*]-(w2:Word))
	WHERE w1.word = 'they' AND w2.word = 'themselves'
	RETURN p

	MATCH p = ALL((w1:Word)-[:CONTAINS*]-(w2:Word))
	WHERE w1.word = 'they' AND w2.word = 'themselves'
	RETURN p order by length(p) limit 10

	MATCH p = ALL((w1:Word)-[*]-(w2:Word))
	WHERE w1.word = 'they' AND w2.word = 'themselves'
	RETURN p order by length(p) limit 10

	MATCH p = ALL((w1:Word)-[]-(w2:Word))
	WHERE w1.word = 'they' AND w2.word = 'themselves'
	RETURN p

	MATCH p=(a)-[*]->(b)
	RETURN p

6. 删除节点

	MATCH (n:Label {name:'NodeName'})
	DETACH DELETE n

	MATCH (w:Word {word:'hello'})
	DETACH DELETE w

7. 查询节点

	MATCH (n:Word {word:'the'})
	RETURN n

	MATCH (n:Word {word:'hello'})
	RETURN n

8. 查看版本

	CALL dbms.components()
		["5.10.0"]

9. 查询某个节点的最近节点关系

    MATCH (start:Word {word:'the'})
    MATCH path = (start)-[*2]-(end)
    RETURN end.word


    MATCH (start:Word {word:'the'})
    MATCH path = (start)-[*2]-(end)
    RETURN DISTINCT end.word


    MATCH (start:Word {word:'mathematical'})
    MATCH path = (start)-[*2]-(end)
    RETURN DISTINCT end.word

    MATCH (start:Word {word:'the'})
    MATCH path = (start)-[*2..7]-(end)
    RETURN DISTINCT end.word

    MATCH (start:Word {word:'the'})
    MATCH path = (start)-[*5..7]-(end)
    RETURN DISTINCT end.word

    MATCH (start:Word {word:'the'})
    MATCH path = (start)-[*2..7]-(end)
    RETURN end.word, length(path) AS distance

### 自己建立关系和CRUD等操作

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
2. <https://neo4j.com/docs/getting-started/get-started-with-neo4j/>
3. <https://neo4j.com/docs/getting-started/cypher-intro/>
4. <https://neo4j.com/docs/getting-started/cypher-intro/patterns-in-practice/>
5. <https://neo4j.com/docs/getting-started/cypher-intro/updating/>
6. <https://blog.csdn.net/u011250186/article/details/107234087>
7. <https://blog.csdn.net/wavehaha/article/details/111592161>
