# SQL

### SQL 简介

**SQL**（[![聆听](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3b/Speakerlink-new.svg/11px-Speakerlink-new.svg.png)](https://upload.wikimedia.org/wikipedia/commons/5/5f/En-us-SQL.ogg)**[i](https://zh.wikipedia.org/wiki/File:En-us-SQL.ogg)**[/ˈɛs kjuː ˈɛl/](https://zh.wikipedia.org/wiki/Help:英語國際音標)[[4]](https://zh.wikipedia.org/wiki/SQL#cite_note-learningSQL-4)或[![聆听](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3b/Speakerlink-new.svg/11px-Speakerlink-new.svg.png)](https://upload.wikimedia.org/wikipedia/commons/7/7a/En-us-sequel.ogg)**[i](https://zh.wikipedia.org/wiki/File:En-us-sequel.ogg)**[/ˈsiːkwəl/](https://zh.wikipedia.org/wiki/Help:英語國際音標)][[5]](https://zh.wikipedia.org/wiki/SQL#cite_note-5)，**Structured Query Language:结构化查询语言**[[6\]](https://zh.wikipedia.org/wiki/SQL#cite_note-6)[[7\]](https://zh.wikipedia.org/wiki/SQL#cite_note-7)[[8\]](https://zh.wikipedia.org/wiki/SQL#cite_note-8)[[9\]](https://zh.wikipedia.org/wiki/SQL#cite_note-9)）是一种[特定目的编程语言](https://zh.wikipedia.org/wiki/特定目的程式语言)，用于管理[关系数据库管理系统](https://zh.wikipedia.org/wiki/关系数据库管理系统)（RDBMS），或在[关系流数据管理系统](https://zh.wikipedia.org/wiki/关系流数据管理系统)（RDSMS）中进行流处理。

**SQL** ([/ˌɛsˌkjuːˈɛl/](https://en.wikipedia.org/wiki/Help:IPA/English) ([![About this sound](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8a/Loudspeaker.svg/11px-Loudspeaker.svg.png)](https://en.wikipedia.org/wiki/File:En-us-SQL.ogg)[listen](https://upload.wikimedia.org/wikipedia/commons/5/5f/En-us-SQL.ogg)) *S-Q-L*,[[4\]](https://en.wikipedia.org/wiki/SQL#cite_note-learningSQL-4) [/ˈsiːkwəl/](https://en.wikipedia.org/wiki/Help:IPA/English) "sequel"; **Structured Query Language**)[[5\]](https://en.wikipedia.org/wiki/SQL#cite_note-Britannica-5)[[6\]](https://en.wikipedia.org/wiki/SQL#cite_note-oed-US-6)[[7\]](https://en.wikipedia.org/wiki/SQL#cite_note-MS-SQL-def-7) is a [domain-specific language](https://en.wikipedia.org/wiki/Domain-specific_language) used in programming and designed for managing data held in a [relational database management system](https://en.wikipedia.org/wiki/Relational_database_management_system) (RDBMS), or for stream processing in a [relational data stream management system](https://en.wikipedia.org/wiki/Relational_data_stream_management_system) (RDSMS). It is particularly useful in handling [structured data](https://en.wikipedia.org/wiki/Data_model), i.e. data incorporating relations among entities and variables.

SQL基于[关系代数](https://zh.wikipedia.org/wiki/关系代数_(数据库))和[元组关系演算](https://zh.wikipedia.org/wiki/元组关系演算)，包括一个[数据定义语言](https://zh.wikipedia.org/wiki/数据定义语言)和[数据操纵语言](https://zh.wikipedia.org/wiki/数据操纵语言)。SQL的范围包括数据插入、查询、更新和删除，[数据库模式](https://zh.wikipedia.org/wiki/Schema_(数据库))创建和修改，以及数据访问控制。尽管SQL经常被描述为，而且很大程度上是一种[声明式编程](https://zh.wikipedia.org/wiki/声明式编程)（[4GL](https://zh.wikipedia.org/wiki/第四代程式語言)），但是其也含有[过程式编程](https://zh.wikipedia.org/wiki/过程式编程)的元素。

Originally based upon [relational algebra](https://en.wikipedia.org/wiki/Relational_algebra) and [tuple relational calculus](https://en.wikipedia.org/wiki/Tuple_relational_calculus), SQL consists of many types of statements,[[8\]](https://en.wikipedia.org/wiki/SQL#cite_note-8) which may be informally classed as [sublanguages](https://en.wikipedia.org/wiki/Sublanguage), commonly: a [data query language](https://en.wikipedia.org/wiki/Data_query_language) (DQL),[[a\]](https://en.wikipedia.org/wiki/SQL#cite_note-9) a [data definition language](https://en.wikipedia.org/wiki/Data_definition_language) (DDL),[[b\]](https://en.wikipedia.org/wiki/SQL#cite_note-10) a [data control language](https://en.wikipedia.org/wiki/Data_control_language) (DCL), and a [data manipulation language](https://en.wikipedia.org/wiki/Data_manipulation_language) (DML).[[c\]](https://en.wikipedia.org/wiki/SQL#cite_note-11)[[9\]](https://en.wikipedia.org/wiki/SQL#cite_note-12) The scope of SQL includes data query, data manipulation (insert, update and delete), data definition ([schema](https://en.wikipedia.org/wiki/Database_schema) creation and modification), and data access control. Although SQL is essentially a [declarative language](https://en.wikipedia.org/wiki/Declarative_programming) ([4GL](https://en.wikipedia.org/wiki/4GL)), it includes also [procedural](https://en.wikipedia.org/wiki/Procedural_programming) elements.

当前，所有主要的关系数据库管理系统支持某些形式的SQL，大部分数据库至少遵守`ANSI SQL89`标准。

`ANSI SQL92`标准在交叉连接（cross join）和内部连接之上，新增加了外部连接，并支持在`FROM`子句中写连接表达式。支持集合的并运算、交运算。支持[`Case (SQL)`](https://zh.wikipedia.org/wiki/Case_(SQL))表达式。支持`CHECK`约束。创建临时表。支持`cursor`。支持[事务隔离](https://zh.wikipedia.org/wiki/事務隔離)。

### SQL 分类

SQL包含四个部分：

- [数据定义语言](https://zh.wikipedia.org/wiki/資料定義語言)
- [数据操纵语言](https://zh.wikipedia.org/wiki/資料操縱語言)
- [数据控制语言](https://zh.wikipedia.org/wiki/資料控制語言)
- [事务控制语言](https://zh.wikipedia.org/wiki/事务控制语言)

### SQL 语法

- 子句，是语句和查询的组成成分。（在某些情况下，这些都是可选的。）[[14\]](https://zh.wikipedia.org/wiki/SQL#cite_note-14)
- 表达式，可以产生任何[标量](https://zh.wikipedia.org/wiki/变量_(程序设计))值，或由[列](https://zh.wikipedia.org/wiki/列_(資料庫))和[行](https://zh.wikipedia.org/wiki/行_(資料庫))的[数据库表](https://zh.wikipedia.org/wiki/数据库表)
- 谓词，给需要评估的SQL[三值逻辑（3VL）](https://zh.wikipedia.org/wiki/三值逻辑)（true/false/unknown）或[布尔](https://zh.wikipedia.org/wiki/逻辑代数)[真值](https://zh.wikipedia.org/wiki/真值)指定条件，并限制语句和查询的效果，或改变程序流程。
- 查询，基于特定条件检索数据。这是*SQL*的一个重要组成部分。
- 语句，可以持久地影响纲要和数据，也可以控制数据库事务、程序流程、连接、会话或诊断。
  - SQL语句也包括[分号](https://zh.wikipedia.org/wiki/分號)（";"）语句终结符。尽管并不是每个平台都必需，但它是作为SQL语法的标准部分定义的。
- [无意义的空白](https://zh.wikipedia.org/wiki/空白)在SQL语句和查询中一般会被忽略，更容易格式化SQL代码便于阅读。

- *Clauses*, which are constituent components of statements and queries. (In some cases, these are optional.)[[18\]](https://en.wikipedia.org/wiki/SQL#cite_note-ANSI/ISO/IEC-21)
- *Expressions*, which can produce either [scalar](https://en.wikipedia.org/wiki/Scalar_(computing)) values, or [tables](https://en.wikipedia.org/wiki/Table_(database)) consisting of [columns](https://en.wikipedia.org/wiki/Column_(database)) and [rows](https://en.wikipedia.org/wiki/Row_(database)) of data
- *Predicates*, which specify conditions that can be evaluated to SQL [three-valued logic (3VL)](https://en.wikipedia.org/wiki/Ternary_logic) (true/false/unknown) or [Boolean](https://en.wikipedia.org/wiki/Boolean_logic) [truth values](https://en.wikipedia.org/wiki/Truth_value) and are used to limit the effects of statements and queries, or to change program flow.
- *Queries*, which retrieve the data based on specific criteria. This is an important element of *SQL*.
- Statements, which may have a persistent effect on schemata and data, or may control transactions, program flow, connections, sessions, or diagnostics.
  - SQL statements also include the [semicolon](https://en.wikipedia.org/wiki/Semicolon) (";") statement terminator. Though not required on every platform, it is defined as a standard part of the SQL grammar.
- *[Insignificant whitespace](https://en.wikipedia.org/wiki/Whitespace_(computer_science))* is generally ignored in SQL statements and queries, making it easier to format SQL code for readability.

$$
{\displaystyle \left.{\begin{array}{rl}\textstyle {\mathtt {UPDATE~clause}}&\{{\mathtt {UPDATE\ country}}\\\textstyle {\mathtt {SET~clause}}&\{{\mathtt {SET\ population=~}}\overbrace {\mathtt {population+1}} ^{\mathtt {expression}}\\\textstyle {\mathtt {WHERE~clause}}&\{{\mathtt {WHERE\ \underbrace {{name=}\overbrace {'USA'} ^{expression}} _{predicate};}}\end{array}}\right\}{\textstyle {\texttt {statement}}}}
$$

### SQL语句能做什么

- SQL 面向数据库执行查询
- SQL 可从数据库取回数据
- SQL 可在数据库中插入新的记录
- SQL 可更新数据库中的数据
- SQL 可从数据库删除记录
- SQL 可创建新数据库
- SQL 可在数据库中创建新表
- SQL 可在数据库中创建存储过程
- SQL 可在数据库中创建视图
- SQL 可以设置表、存储过程和视图的权限