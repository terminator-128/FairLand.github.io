# SQL Tutorial

> SQL虽然是门结构化的语言，但大多数教程其基础知识点组织还是比较零散的、碎片化的。
>
> 假定宁的电脑上已经成功安装DBMS，这里从功用的角度快速地使用SQL进行所需的操作。（示例实验使用 mysql 8.0 command line client，实验使用的示例不与真实信息相对应）相关命令操作请查询: [here](https://dev.mysql.com/doc/refman/8.0/en/)

## 创建新数据库

使用的SQL语句：

```sql
CREATE DATEBASE database_name
```

实验示例：

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/SQL_CREATEDATABASE.jpg" style="zoom:80%;" />

结果显示:

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/SQL_AFTER_createdatabase.jpg" style="zoom:80%;" />

## 在数据库中创建新表

使用的SQL语句：

```sql
CREATE TABLE table_name
(
	column_1	datatype_1,
	column_2	datatype_2,
	column_3	datatype_3,
    ···
    column_n	datatype_n
)
```

实验示例：

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/SQL_CREATETABLE.jpg" style="zoom:80%;" />

实验结果：

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/SQLAFTER_CREATETABLE.jpg" style="zoom:80%;" />

> [SQL约束](https://www.w3school.com.cn/sql/sql_constraints.asp)用于限制加入表的数据的类型。可以在创建表时，规定约束（通过`CREATE TABLE`语句）；或在表创建之后也可以（通过`ALTER TABLE`）

```sql
CREATE TABLE Persons
(
姓名 nvarchar(255) PRIMARY KEY,
年龄 tinyint
)
```

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/SQL_CREATETABLE_KEY.jpg" style="zoom:80%;" />

## 在数据库中插入新的记录

在数据库中插入新的记录使用`INSERT`标记：

**（1）插入数据行：**

```sql
INSERT INTO table_name (value_1,value_2,···,value_n)
```

实验示例：

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/SQL_INSERTINTO.jpg" style="zoom:80%;" />

实验结果：

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/SQL_AFTER_INSERTINTO.jpg" style="zoom:80%;" />

**（2）在指定的里插入数据：**

```sql
INSERT INTO table_NALE (column_1,column_2,···,column_n) VALUES (value_1,value_2,···,value_n)
```

实验示例：

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/SQL_INSERTINTO_2.jpg" style="zoom:80%;" />

运行结果：

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/SQL_AFTER_INSERTINTO_2.jpg" style="zoom:80%;" />

> 1. 在INSERT插入时如果没有设置主键是允许重复的；
> 2. 如果插入数据主键在表中已存在，则插入数据失败。

## 面向数据库执行查询

数据库的查询需要 `SELECT` 语句：

```sql
SELECT [ALL(defalut)| DISTINCT ] <column_expression>,[, <column_expression>···]
FROM <table_expression>[, <table_expression>···]
INNER/LEFT/RIGHT/FULL JOIN another_table
ON	connect_condition
WHERE filter_condition(s){towards records}
GROUP BY column_tuple
Having 	filter_condition{towards groups}
ORDER BY <column ASC/DESC>,···
LIMIT num_limit OFFSET num_offset
```

整个SELECT语句含义是（按执行顺序）：

- 根据FROM子句对引用的各个基本表、视图或派生表中的元组做笛卡尔积。
- 根据JOIN ON子句根据条件与选择的方式进行表的连接。
- 根据WHERE子句中的条件对从FROM子句生成的元组集做筛选。
- 根据SELECT子句对目标表达式(column_expression)选出元祖中的属性值形成结果表。
- 根据GROUP BY子句，将结果按元组向量相等为依据进行分组。
- 根据HAVING子句（配合GROUP BY使用），对GROUP BY子句形成的组按条件筛选输出（通常会在每组中作用聚焦函数）
- 根据ORDER BY子句，将结果表按照元组向量属性值从左向右按照要求的排序方式[升序ASC(default)、降序DESC]排序。
- 根据LIMIT num_limit OFFSET num_offset，将结果表从OFFSET为num_offset（包含num_offset记录，首条记录OFFSET为0）开始取 num_limit 条记录。

> 看着很麻烦，但正如README中所说，SQL由组成的具有优先级的子句组成，每个字句都是简单的命令，下面分子句标志进行梳理。

---

### SELECT  FROM

```sql
SELECT [ALL(defalut)| DISTINCT ] <column_expression>,[, <column_expression>···]
FROM <table_expression>[, <table_expression>···]
```

> SELECT 限定符一般不去重（`ALL`），使用 `DISTINCT`可以去除数据重复行。

其中，列表达式\<column_express\>不仅可以是算术表达式，可以进行一系列easy数学（+-*/）计算，还可以是字符串常量、函数等。

> 例如：\<column_expression\>的一个例子可以为
>
> ```sql
> /*1. 按权重计算总成绩*/
> SELECT (0.2*grade_1+0.8*grade_2) AS final_grade
> /*2. 查询全体学生的姓名、出生年份、所在院系*/
> SELECT Sname, (2014-Sage) AS 'Year of Birth' , LOWER(Sdept)
> ```
>
> 其中，(1) 将计算出来的成绩以`final_grade作为别名；(2) 三个字段分别为姓名，出生年份、所在院系（使用字符串小写函数LOWER(string)）

其中，\<table_expression\>可以为基本表、子查询得到的表、创建的视图（本质相当于子查询），其次还可以使用别名（可以使用 AS关键字:joy:也可以不使）。

```sql
/*将一张表复制得到两个内容相同的表进行之后操作*/
SELECT *
FROM table0 AS t1,table0 AS t2
```

---

### JOIN	ON

一般关系数据表中，都有一个属性设置为 **主键(primary key)**，借助主键或其他唯一性的属性，可以将两个表中具有相同主键 ID的数据连接起来，合成一条记录。

Join连接一般格式：

```sql
INNER/LEFT/RIGHT/FULL JOIN another_table
ON	connect_condition
```

> 例如，Product表和Sale表中具有相同主键——商品号Cid，想得到每件商品的销售信息
>
> ```sql
> SELECT *
> FROM Product
> JOIN Sale
> ON Product.Cid=Sale.Cid
> ```
>
> 由默认左连接所以可以得到所有商品的销售信息，没有置为NULL。

- INNER  JOIN（ JOIN ）

```sql
(INNER) JOIN anther_table
ON 		connect_condituon
```

> 例如：
>
> ```sql
> SELECT 	*
> FROM 	A
> JOIN 	B
> ON 		A.Pid=B.Pid
> ```
>
> 结果表中的主键C与A、B主键集之间的关系: $C=A\cap B$
>
> <img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/INNER_JOIN.png" style="zoom:100%;" />

- LEFT     JOIN

```sql
LEFT JOIN	another_table
ON 			connnect_id
```

> 例如：
>
> ```sql
> SELECT		*
> FROM 		A
> LEFT JOIN	B
> ON			A.Pid=B.Pid
> ```
>
> 结果表中保留A中的所有行(所有A中主键的记录，B中对应主键记录不存在是结果表中对应B中属性赋值NULL)。
>
> <img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/LEFT_JOIN.png" style="zoom:100%;" />

- RIGHT  JOIN

```sql
LEFT JOIN 	another_table
ON 			connnect_id
```

> 例如：
>
> ```sql
> SELECT		*
> FROM 		A
> RIGHT JOIN	B
> ON			A.Pid=B.Pid
> ```
>
> 结果表中保留B中的所有行(所有B中主键的记录，A中对应主键记录不存在是结果表中对应A中属性赋值NULL)。
>
> <img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/RIGHT_JOIN.png" style="zoom:100%;" />

- FULL    JOIN

```sql
FULL JOIN 	another_table
ON 			connnect_id
```

> 例如：
>
> ```sql
> SELECT		*
> FROM 		A
> FULL JOIN	B
> ON			A.Pid=B.Pid
> ```
>
> 结果表中保留A、B中的所有行(结果集出现A、B中出现的所有主键对应的记录)。
>
> <img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/FULL_JOIN.png" style="zoom:100%;" />

---

### WHERE

WHERE子句一般格式：

```sql
WHERE filter_condition(s){towards records}
```

> WHERE 直接选择符合条件的元组，下表是WHERE常用的查询条件：

<table style="font-family:Times New Roman,宋体">
    <tr>
        <th align="center">查询条件</th>
        <th align="center">谓词</th>
    </tr>
    <tr>
        <td align="left">比较</td>
        <td align="left">=, >, <, >=, <=, !=, <>, !>, !<; NOT+上述比较运算符</td>
    </tr>
    <tr>
        <td align="left">确定范围</td>
        <td align="left">BETWEEN AND, NOT BETWEEN AND</td>
    </tr>
    <tr>
        <td align="left">确定集合</td>
        <td align="left">IN, NOT IN</td>
    </tr>
    <tr>
        <td align="left">字符匹配</td>
        <td align="left">LIKE, NOT LIKE</td>
    </tr>
    <tr>
        <td align="left">空值</td>
        <td align="left">IS NULL, IS NOT NULL</td>
    </tr>
    <tr>
        <td align="left">多重运算（逻辑运算）</td>
        <td align="left">AND, OR, NOT</td>
    </tr>
            </table>


- 比较大小
  用于进行比较的运算符一般包括 = (等于), > (大于), < (小于), >=(大于等于), <=(小于等于),  != 或 <> (不等于) , !> (不大于) , !< (不小于) 。

- 确定范围

  谓词`BETWEEN···AND···`和`NOT BETWEEN···AND···`可以用来查找属性值在（或不在）指定范围的元组，其中`BETWEEN`后是范围的下限（即低值），`AND`后是范围的上限（即高值）。

- 确定集合

  谓词`IN`可以用来查找属性值属于指定集合的元组；谓词`NOT IN`用来查找属性值不属于指定集合的元组。

- 字符匹配

  谓词`LIKE`可以用来进行字符串的匹配。其一般语法格式如下：
  
  ```sql
  [NOT] LIKE '<匹配串>' [ESCAPE '<换码字符>']
  ```
  
  其含义是查找指定的属性列值与<匹配串>相匹配的元组。
  
  <匹配串>可以是一个完整的字符串，也可以含有通配符 % 和 _ 。其中：
  
  - %（百分号）代表任意长度（长度可以为0）的字符串。
  
  - _ （下横线）代表任意单个字符。
  
    > 这就哦数据库字符集为ASCII是一个汉字需要两个 _ ；当字符集为GBK时只需要一个 _ 。
  
  如果用户查询的字符串本身就好友通配符 % 或 _ ，这是就要使用 ESCAPE ‘<换码字符>’ 短语对通配符进行转义。
  
  > 例如：查询DB_Design课程的课程号和学分
  >
  > ```sql
  > SELECT Cno,Ccredit
  > FROM Course
  > WHERE Cname LIKE 'DB\_Design' ESCAPE '\';
  > ```
  >
  > ESCAPE ' \\ '表示 " \\ "为换码字符，这样紧跟在" \\ "后面的字符" _ "就不会再具有通配符的含义，转一位普通的" _ " 字符。
  
- 涉及空值的查询

  > 例如：查询缺考的学生学号和相应的课程号：
  >
  > ```sql
  > SELECT Sno,Cno
  > FROM SC
  > WHERE Grade IS NULL
  > ```
  >
  > 注意：这里的"IS" 不能用等号"="代替。

- 多重条件查询

  逻辑运算符 `AND` 和 `OR` 可以用来连接多个查询条件。`AND` 的优先级高于 `OR` ，单用户可以用括号改变优先级。

  > 例如：
  >
  > ```sql
  > WHERE Grade>60 AND Name LIKE '夏%' OR Class LIKE 'B_'
  > ```

---

### GROUP BY

GROUP BY子句将查询结果某一列或多列的值（行向量）分组，值相等的为一组。

> 得到所有选课学生的学号：
>
> ```sql
> SELECT 		Sid
> FROM		Student
> GROUP BY 	Sid
> ```
>
> 其实这样的问题也可以用 DISTINCT 关键字解决。但GROUP BY的左右不止于此。

对查询结果分组的目的是为了细化聚集函数的作用对象。

> 如果未对查询结果分组，聚集函数将作用于整个查询结果；分组后聚集函数姜作勇每一个组，即每一个组都有一个函数值。

常见的聚集函数如下表：

<table style="font-family:Times New Roman,宋体">
	<tr>
        <td align="left">COUNT(*)</td>
        <td aling="left">统计元组个数</td>
    </tr>
    <tr>
        <td align="left">COUNT([DISTINCT|ALL] <列名>)</td>
        <td aling="left">统计一列中值的个数</td>
    </tr>
    <tr>
        <td align="left">SUM([DISTINCT|ALL] <列名>)</td>
        <td aling="left">统计一列中值的个数</td>
    </tr>
    <tr>
        <td align="left">AVG([DISTINCT|ALL] <列名>)</td>
        <td aling="left">计算一列值的平均值（此列必须是数值型）</td>
    </tr>
    <tr>
        <td align="left">MAX([DISTINCT|ALL] <列名>)</td>
        <td aling="left">求一列值中的最大值</td>
    </tr>
    <tr>
        <td align="left">MAX([DISTINCT|ALL] <列名>)</td>
        <td aling="left">求一列值中的最小值</td>
    </tr>
            </table>

> 如果指定DISTINCT关键字，则在计算前先对列元组中重复行值进行去重，再在作用以聚焦函数；如果不指定DISTINCT（ALL为默认值）或指定ALL，则表示不取消重复值。
>
> 例：查询每门课程选修的人数
>
> ```sql
> SELECT 	Sno,Sname,COUNT(DISTINCT Sno)
> FROM 	SC
> GROUP BY Sno;
> ```
>
> 例：查询每个班的平均分
>
> ```sql
> SELECT 	Cno,AVG(Grade)
> FROM	Result
> GROUP BY Cno;
> ```

当聚焦函数遇到空值时，除 COUNT(*) 外，都跳过空值而只处理非空值。

> 因为 COUNT(*) 是对元组计数，故某元组进行计数，某元组的一个或部分列去空值不影响其统计结果

**注意**：由于执行顺序问题（优先级），`WHERE`总不可出现聚焦函数，聚焦函数只可出现在`SELECT`子句和`ORDER BY`子句和`GROUP BY`中的`HAVING`子句。下面是`HAVING`的格式：

```sql
HAVING 	filter_condition{towards groups}
```

`HAVING`将对`GROUP BY`分得的组进行筛选。

> 例：查询班级平均分高于95分的班级
>
> ```sql
> SELECT 	Cno
> FROM	Result
> GROUP BY Cno
> HAVING 	AVG(Grade)>95;
> ```

---

### ORDER BY

用户可以用`ORDER BY`子句对查询结果进行排序（ASC）或降序（DESC），默认值为升序。

```sql
ORDER BY <column ASC/DESC>,···
```

> 对于空值，排序时显示的次序由具体的系统实现来决定。各个系统实现可以不同，只要保持一致就行。
>
> 例如：依照先按成绩降序排序，成绩相同再按字母序排序
>
> ```sql
> SELECT *
> FROM Student
> ORDER BY Grade DESC, Name Asc
> ```

由于`ORDER BY`的优先级较低（低于`GROUP BY`），所以可以对聚焦函数作用后的列进行排序。

---

### LIMIT OFFSET

当排序完成后，我们想要达到序列中从第几个开始的几个行记录，可以使用`LIMIT OFFSET`。

```sql
LIMIT num_limit OFFSET num_offset
```

> `LIMIT`后的num_limit 代表所需结果表中的行记录的条数，`OFFSET`后的是从第几条记录开始（第一条记录num_offset为0）。

实验示例：得到下表成绩第二名

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/LIMIT_PRE.jpg" style="zoom:100%;" />

```sql
SELECT *
FROM pc.RESULT
ORDER BY 成绩
LIMIT 1 OFFSET 1;
```

运行结果：

<img src="https://github.com/terminator-128/FairLand.github.io/raw/master/pictures/LIMIT_AFTER.jpg" style="zoom:100%;" />

---

### 嵌套查询

在 SQL 语言中，一个 SELECT-FROM-WHERE 语句称为一个查询块。将一个查询块嵌套在另一个查询块的 WHERE 子句或 HAVING 短语的条件中的查询称为嵌套查询（nested query）。

> 外层的查询块称为外层查询或父查询，内层的查询块称为内层查询或子查询（subquery）。

SQL语言允许多层嵌套查询，即一个子查询中还可以嵌套其他子查询。

> 注意，子查询的 `SELECT` 语句不能使用 `ORDER BY` 子句，`ORDER BY` 子句只能对最终查询结果排序。

#### （1）子查询的谓词分类

根据谓词的使用，子查询可以分为以下几类：

- 带有 IN 谓词的子查询
- 带有比较运算符的子查询
- 带有 ANY（SOME）或 ALL 谓词的子查询
- 带有 EXISTS 谓词的子查询

**（1） 带有 IN 谓词的子查询**

​	在嵌套查询中，子查询结果往往是一个集合，所以谓词IN是嵌套查询中最经常使用的谓词，但要注意的是需要条目对齐（行记录属性值顺序对应域相同）。

> 例：查询与“刘晨”在同一个系学习的学生
>
> > 先分步来完成次查询，然后在构造嵌套查询
>
> 查询使用的SQL语句为：
>
> ```sql
> SELECT 	Sno,Sname,Sdept
> FROM 	Student
> WHERE 	Sdept IN (SELECT Sdept
>                   FROM	Student
>                  WHERE Sname="刘晨")
> ```
>
> 此嵌套语句不依赖于父查询，属于不相关子查询，相当于执行两步查询。
>
> > 子查询的结果用于建立其父查询的查找条件。
>
> - 确定“刘晨”所在系名
>
>   ```sql
>   SELECT Sdept
>   FROM Student
>   WHERE Sname='刘晨'
>   ```
>
>   结果为 'CS'
>
> - 查找所有在'CS'系学习的学生
>
>   ```sql
>   SELECT 	Sno,Sname,Sdept
>   FROM	Student
>   WHERE	Sdept='CS'
>   ```

**（2） 带有比较运算符的子查询**

​	带有比较运算符的子查询是父查询与子查询之间用比较预算符进行连接运算。

> <u>当用户能确切知道内层查询返回的是单个值时，可以用 >、<、=、>=、<=、!=或<>等比较运算符</u>，举例如下：
>
> ```sql
> SELECT 	Sno,Sname,Sdept
> FROM	Student
> WHERE	Sdept = 
> 			(SELECT Sdept
>              FROM	Student
>              WHERE	Sname='刘晨');
> ```

**（3）带有ANY（SOME）或 ALL 谓词的子查询**

​	子查询返回但只是可以用比较运算符，但返回多值是要用 ANY（用的系统用SOME）或 ALL 谓词修饰符。而<u>使用ANY 或 ALL 谓词时必须同时使用比较运算符</u>。其语义如下所示：

<table style="font-family:Times New Roman,宋体">
	<tr>
        <td align="left">> ANY</td>
        <td aling="left">大于子查询结果中的某个值</td>
    </tr>
	<tr>
        <td align="left">> ALL</td>
        <td aling="left">大于子查询结果中的所有值</td>
    </tr>
    <tr>
        <td align="left">< ANY</td>
        <td aling="left">小于子查询结果中的某个值</td>
    </tr>
    <tr>
        <td align="left">< ALL</td>
        <td aling="left">小于子查询结果中的所有值</td>
    </tr>
    <tr>
        <td align="left">>=ANY</td>
        <td aling="left">大于等于子查询结果中的某个值</td>
    </tr>
	<tr>
        <td align="left">>=ALL</td>
        <td aling="left">大于等于子查询结果中的所有值</td>
    </tr>
    <tr>
        <td align="left"><=ANY</td>
        <td aling="left">小于等于子查询结果中的某个值</td>
    </tr>
    <tr>
        <td align="left"><=ALL</td>
        <td aling="left">小于等于子查询结果中的所有值</td>
    </tr>
    <tr>
        <td align="left">=ANY</td>
        <td aling="left">等于子查询结果中的某个值</td>
    </tr>
    <tr>
        <td align="left">=ALL</td>
        <td aling="left">等于子查询结果中的所有值</td>
    </tr>
    <tr>
        <td align="left">!=(或<>)ANY</td>
        <td aling="left">不等于子查询结果中的某个值</td>
    </tr>
    <tr>
        <td align="left">!=(或<>)ALL</td>
        <td aling="left">不等于子查询结果中的任何一个值</td>
    </tr>
            </table>

> 此处不一一例证了——太多了（汗:tired_face: ）。
>
> ANY、ALL、与聚焦函数、谓词IN有着奇妙的对性关系，由于本篇不涉及调优，所以暂时不涉及对等价关系的证明，有闲工夫的阔以自己去探索这种等价转换关系:grinning:。

**（4）带有EXISTS 谓词的子查询**

​	EXISTS 代表存在量词 $\exists$ 。<u>带有 EXISTS 谓词的子查询不返回任何数据，只产生逻辑真值 "true"或逻辑假值"flase"。</u>

>  可以用EXISTS 来判断 $x\in S、S \sube R、S=R、S\cap R$非空等时候成立

下面来通过三个个例子来介绍EXISTS的使用：

1. 查询所有选修了1号课程的学生姓名。
   $$
   \begin{align}
   &p:学生\\
   &q:一号课程\\
   &R:选修关系\\
   &则欲通过查询求得的结果集S满足：\forall p \in S,\ pRq\\
   
   \end{align}
   $$

   >  本次查询涉及 Student 和 SC 表，我们可以这么转化问题，对Student中所有学生，如果存在学生 $p$ 满足 $pRq$ 则使用EXISTS的相关子查询将选择结果判定为真，从而得到所需的最终结果集

   所以SQL查询语句可写为：

   ```sql
   SELECT	Sname
   FROM	Student
   WHERE	EXISTS (SELECT *
                	FROM SC
                	WHERE Sno=Student.Sno AND Cno='1');
   ```

   > 这个子查询的处理过程是：首先去外层查询中 Student 表的第一个元组，根据它与内层查询相关的属性值（Sno值）处理内层查询，若WHERE子句返回值为真，则去外层查询中该元组的Sname放入结果表；然后再取Student表的下一个元组；重复这一过程，直至外层Student表全部检查完为止。

2. 查询选修了全部课程的学生姓名。($\forall$的转换)
   $$
   (\forall x)P \equiv \neg (\exist x(\neg P))
   $$

   > 由上述数理逻辑中的逻辑定理，我们可以对问题进行转换成等价的用存在量词的形式。所以，查询这样的学生满足——没有一门课程是他不选修的。

   查询对应的SQL语句可写为：

   ```sql
   SELECT 	Sname
   FROM	Student
   WHERE	NOT EXISTS
   		(SELECT *
            FROM Course
            WHERE NOT EXISTS
            		(SELECT *
                    FROM SC
                    WHERE Sno=Student.Sno AND Cno=Course.Cno))
   ```

3. 查询至少选修了学生2012115122选修的全部课程的学生号码。

   > 本查询可以用逻辑蕴涵来表达；查询学号为 $x$ 的学生，对所有的课程 $y$ ，只要 2012155122学生选修了课程 $y$ ，则 $x$ 也选修了 $y$ 。形式化表达如下：

   $$
   \begin{align}
   &y(变量):课程\\
   &p(谓词):学生201215122选择了课程y\\
   &q(谓词):学生x选择了课程y\\
   &则上述查询为:\ (\forall y)p\to q\\
   \end{align}
   $$

   由于SQL语言中没有蕴含(implication)，即$\to$的逻辑运算，可以用谓词演算将一个逻辑蕴含的为此等价转换。
   $$
   p\to q \equiv \neg p \vee q
   $$

   > 按照上述定理，$(\forall\ y)p \to q \equiv \exist\ y(p \wedge \neg q) $
   >
   > 其表达的语义是：不存在这样的课程 $y$ ，学生201215122选修了 $y$ ，而学生 $x$ 没有选。

   查询用SQL语言表示如下：

   ```sql
   SELECT DISTINCT Sno
   FROM SC SCX
   WHERE NOT EXISTS
   	  (SELECT *
          FROM SC SCY
          WHERE SCY.Sno='201215122'.AND NOT EXISTS
          								 (SELECT *
                                         FROM SC SCZ
                                         WHERE SCZ.Sno=SCX.Sno AND SCZ.Cno=SCY.Cno));
   ```

#### （2）子查询父类相关性

嵌套查询中的子查询还可依据是否与父类相关分为两类：

- **不相关子查询**——子查询的查询条件不依赖父母

  > 可以考虑用连接查询替代，在WHERE中用多个等值查询解决。
  >
  > 举例见 ”带有IN谓词的子查询“ 条目。

- **相关子查询**（correlated subquery）——子查询的查询条件依赖于父查询

  > 这类嵌套查询很难或不能用WHERE中连接运算替代。
  >
  > 例如：找出每个学生超出他自己选修课程平均成绩的课程号
  >
  > ```sql
  > SELECT 	Sno,Cno
  > FROM 	SC x
  > WHERE	Grade >=(SELECT AVG(GRADE)
  >                  FROM	SC y
  >                  WHERE y.Sno=x.Sno);
  > ```
  >
  > 解读如下：
  >
  > 对于x中的一条记录，取其中的属性Sno，在子查询中的所有行寻找与其对应属性值相等的y.Sno，产生的子表再通过对整个表的元组属性GRADE做聚集函数AVG()计算，得到平均值，之后进行比较判断。

  有举例可知，求解相关子查询不能像求解不相关子查询那样一次将子查询求解出来，然后求解父查询。由于内从查询与外层有关，必须反复求值（一般是聚焦函数的值）。

  具有相关子查询的整个查询语句称为**相关嵌套查询**（correlated nested query）。

---

### 集合查询




## 从数据库取回数据

## 更新数据库中的数据

## 从数据库删除记录

## 可在数据库中创建存储过程

## 可在数据库中创建视图

## 可以设置表、存储过程和视图的权限