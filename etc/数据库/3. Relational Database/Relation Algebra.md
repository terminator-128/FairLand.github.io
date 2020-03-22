# 关系代数

关系代数是一种抽象的查询语言，他对关系的运算来表达查询。

> 任何一种预算都是将一定的运算符作用于一定的运算对象上，得到预期的运算结果。所以运算对象、运算符、运算结果是运算的三大要素。

关系代数的运算对象是关系，运算结果亦为关系。

> 欧式空间？（雾）——菜鸡作者hhh

关系代数用到的运算符包括两类：集合运算符和专门的关系运算符。

<table style="width:90%" align=center >
	<tr>
        <th colspan="2"  align="center">运算符</th>
        <th  align="center">含义</th>
    </tr>
    <tr>
        <th rowspan="4" align="center">集合</br>运算符</th>
        <td align="center">∪</td>
		<td align="center">并</td>
    </tr>
    <tr>
        <td align="center">-</td>
        <td align="center">差</td>
    </tr>
	<tr>
        <td align="center">∩</td>
        <td align="center">交</td>
    </tr>
	<tr>
        <td align="center">×</td>
        <td align="center">笛卡尔积</td>
    </tr>
	<tr>
        <th rowspan="4" align="center">专门的</br>关系</br>运算符</th>
        <td align="center">σ</td>
		<td align="center">选择</td>
    </tr>
    <tr>
        <td align="center">Π</td>
        <td align="center">投影</td>
    </tr>
	<tr>
        <td align="center">⋈</td>
        <td align="center">连接</td>
    </tr>
	<tr>
        <td align="center">÷</td>
        <td align="center">除</td>
    </tr>
</table>

关系代数的运算按运算符的不同可划分为传统的集合运算和专门的关系运算两类。

- 传统的集合运算将关系看成元组的集合，其运算是从关系的“水平”方向，即行的角度进行

- 专门的关系运算不仅涉及行，而且涉及列。

  > 比较运算符和逻辑运算符是用来辅助专门的关系运算符进行操作的。





---

### 1. 传统的集合运算

> 传统的集合运算是二目运算，包括并、差、交、笛卡尔积

设关系 $R$ 和关系 $S$ 具有相同的目 $n$（即两个关系都有$n$个属性），且相应的属性取自同一个域，$t$ 是元组变量，$t\in R$ 表示 $t$ 是 $R$ 的一个元组。

可以定义 并、差、交、笛卡尔积 运算如下：

##### （1）并（union）

​	关系 $R$ 和关系 $S$ 的并记作
$$
R\cup S =\{ t \mid t \in R \lor t \in S  \}
$$
其结果仍然为 $n$ 目关系，由属于 $R$ 或属于 $S$ 的元组组成。

##### （2）差（except  $\Rightarrow$ difference ）

​	关系 $R$ 和关系 $S$ 的差记作
$$
R-S =\{ t \mid t \in R \land t \notin S  \}
$$
其结果仍然为 $n$ 目关系，由属于 $R$ 而不属于 $S$ 的元组组成。

##### （3）交（intersection）

​	关系 $R$ 和关系 $S$ 的交记作
$$
R \cap S =\{ t \mid t \in R \land t \in S  \}
$$
其结果仍然为 $n$ 目关系，由属于 $R$ 且属于 $S$ 的元组组成。

> 关系的交可以用差来表示： $R \cap S=R-(R-S)$

##### （4）笛卡尔积（Cartesian product）

> 这里的笛卡尔积严格地讲应该是**广义的**笛卡尔积（extended Cartesian product），因为这里笛卡尔积的元素是元组。

两个分别是 $n$ 目和 $m$ 目的关系 $R$ 和关系 $S$ 的笛卡尔积是一个 $(n+m)$ 列的元组的集合。元组的前 $n$ 列是关系 $R$ 的一个元组，后 $m$ 列是关系 $S$ 的一个元组。若 $R$ 有 $k_1$ 个元组，$S$ 有 $k_2$ 个元组，则关系 $R$ 和关系 $S$ 的笛卡尔积有 $k_1 \times k_2$ 个元组。记作
$$
R \times S =\{ \overset{\frown}{t_rt_s} \mid t_r \in R \land t_s \in S  \}
$$
其结果仍然为 $n$ 目关系，由属于 $R$ 且属于 $S$ 的元组组成。

<img src="..\..\..\pictures\Cartesian_product.png" style="width:50%" align="center" />

> <img src="..\..\..\pictures\Cartesian_product_2.png" style="zoom:28%;" align=left />

---



### 2. 专门的关系运算

专门的关系运算包括选择、投影、连接、除运算等。

> 为了叙述上的方便，先引入一下几个符号：
>
> （1）设关系模式为 $R(A_1,A_2,···,A_n)$ ，它的一个关系设为 $R$ 。$t \in R$ 表示 $t$ 是 $R$ 的一个元组。$t[A_i]$ 则表示元组 $t$ 中 中相应于属性 $A_i$ 的一个分量。
>
> （2）若 $A={A_{i1},A_{i2},···,A_{ik}}$，其中 $A_{i1},A_{i2},···,A_{ik}$  是 $A_1,A_2,···,A_n$ 中的一部分，则 $A$ 称为属性列或属性组。$t[A]=(t[A_{i1}],t[A_{i2}],···,t[A_{ik}])$ 表示元组 $t$ 在属性列