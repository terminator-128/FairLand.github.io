# 关系代数:algeria: 

[TOC]

---

关系代数是一种抽象的查询语言，它对关系的运算来表达查询。

> 任何一种预算都是将一定的运算符作用于一定的运算对象上，得到预期的运算结果。所以运算对象、运算符、运算结果是运算的三大要素。

关系代数的运算对象是关系，运算结果亦为关系。

> 欧式空间？（雾）——菜鸡作者hhh

关系代数用到的运算符包括两类：集合运算符和专门的关系运算符。

<table >
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

**:alembic: 本文关系代数内容也可以从[Wiki](https://zh.wikipedia.org/wiki/%E5%85%B3%E7%B3%BB%E4%BB%A3%E6%95%B0_(%E6%95%B0%E6%8D%AE%E5%BA%93)#%E6%8A%95%E5%BD%B1_(%CF%80))详细了解。**

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

> <img src="..\..\..\pictures\Cartesian_product_2.png" style="width:53%;" align=left />

---



### 2. 专门的关系运算

专门的关系运算包括选择、投影、连接、除运算等。

> 为了叙述上的方便，先引入一下几个符号：
>
> （1）设关系模式为 $R(A_1,A_2,···,A_n)$ ，它的一个关系设为 $R$ 。$t \in R$ 表示 $t$ 是 $R$ 的一个元组。$t[A_i]$ 则表示元组 $t$ 中 中相应于属性 $A_i$ 的一个分量。
>
> （2）若 $A=\{A_{i1},A_{i2},···,A_{ik}\}$，其中 $A_{i1},A_{i2},···,A_{ik}$  是 $A_1,A_2,···,A_n$ 中的一部分，则 $A$ 称为属性列或属性组。$t[A]=(t[A_{i1}],t[A_{i2}],···,t[A_{ik}])$ 表示元组 $t$ 在属性列上诸分量的集合，$\overline{A}$ 则表示 $\{A_1,A_2,···,A_n\}$ 中去掉 $\{A_{i1},A_{i2},···,A_{ik}\}$ 后剩余的属性组。
>
> （3）$R$ 为 $n$ 目关系，$S$ 为 $m$ 目关系。$t_r \in R,t_s \in S$ ，$\overset{\frown}{t_rt_s}$ 称为元组的连接（concatenation）或元组的串接。它是一个 $(n+m)$ 列的元组，前 $n$ 个分量是关系 $R$ 中的一个 $n$ 元组，后 $m$ 分量是关系 $S$ 的一个 $m$ 元组。
>
> （4）给定一个关系$R(X,Z)$，$X$ 和 $Z$ 为属性组。当 $t[X]=x$ 时，$x$ 在 $R$ 中的象集（images set）定义为
> $$
> Z_x=\{t[Z] \mid t \in R,t[X]=x\}
> $$
> 它表示 $R$ 中属性组 $X$ 上值为 $x$ 的诸元组在 $Z$ 上分量的集合。  

下面给出专门关系运算的定义：

##### 1. 选择（selection）

选择又称限制（restriction）。它是关系 $R$ 中选择满足给定条件的诸元组，记作
$$
\sigma_F(R)=\{t \mid t \in R \land F(t)=true \}
$$
其中 $F$ 表示选择条件，它是一个逻辑表达式，取逻辑值”true“或“false”。

> 逻辑表达式的基本形式为： $X_1 \theta\ Y_1$ 。
>
> 其中 $\theta$ 表示比较运算符，它可以是 $\gt , \geqslant, \lt,\leqslant,=或\lt\gt $。
>
> <table >
> 	<tr>
>         <th colspan="2"  align="center">运算符</th>
>         <th  align="center">含义</th>
>     </tr>
>     <tr>
>         <th rowspan="5" align="center">比较</br>运算符</th>
>         <td align="center">＞</td>
> 		<td align="center">大于</td>
>     </tr>
>     <tr>
>         <td align="center">≥</td>
>         <td align="center">大于等于</td>
>     </tr>
> 	<tr>
>         <td align="center">＜</td>
>         <td align="center">小于</td>
>     </tr>
> 	<tr>
>         <td align="center">≤</td>
>         <td align="center">小于等于</td>
>     </tr>
> 	<tr>
>         <td align="center">=</td>
>         <td align="center">等于		</td>
>     	</tr>
> 	<tr>
>         <th rowspan="3" align="center">逻辑</br>运算符</th>
>         <td align="center">¬</td>
> 		<td align="center">非</td>
>     </tr>
>     <tr>
>         <td align="center">∧</td>
>         <td align="center">与</td>
>     </tr>
> 	<tr>
>         <td align="center">∨</td>
>         <td align="center">或</td>
>     </tr>
> </table>

> <img src="..\..\..\pictures\selection_relationmodel.png" style="width:39%;" align=left />
>
> <img src="..\..\..\pictures\database_selection_example.png" style="width:50%;" align=left />

---

##### 2. 投影（projection）

关系 $R$ 上的投影是从 $R$ 选择出若干属性列组成的新的关系。记作
$$
\Pi_A(R) = \{ t[A] \mid t \in R \}
$$
其中， $A$ 为 $R$ 中的属性列。

> 由此可见，投影操作是从列的角度进行行的运算。
>
> <img src="..\..\..\pictures\projection_relationmodel.png" style="width:50%;" align=left  />
>
> <img src="..\..\..\pictures\database_projection_example.png" style="width:50%;" align=left />

---

##### 3. [连接](https://zh.wikipedia.org/wiki/%E8%BF%9E%E6%8E%A5#%E8%BF%9E%E6%8E%A5%E7%AE%97%E6%B3%95)（join）

连接也称为 $\theta$ 连接。它是从两个关系的笛卡尔积中选取属性间满足一定条件的元组。记作
$$
R \underset{A\theta B}{\Join} S = \{ \overset{\frown}{t_rt_s} \mid t_r \in R \land t_s \in \land t_r[A] \theta t_s[B] \}
$$
其中，$A$ 和 $B$ 分别是 $R$ 和 $S$ 上列数相等且可比的属性组，$\theta$ 是比较运算符。

> 连接运算从 $R$ 和 $S$ 的笛卡尔积 $R \times S$ 中选取关系在 $A$ 属性组上的值于 $S$ 关系在 $B$ 属性组上的值满足比较关系 $\theta$ 的元组。
>
> <img src="..\..\..\pictures\theta_join_relationAlgbra.png"  style="zoom:28%;" align=left  />
>
> <img src="..\..\..\pictures\theta_join_relationAlgbra2.png"  style="width:39%;" align=left  />

连接运算中两种最为重要最为常用的连接：等值连接、自然连接

###### （1）等值连接（[Equi join](https://www.w3resource.com/sql/joins/perform-an-equi-join.php)）

​	等值连接是 $\theta$ 为 “$=$” 的连接运算，它是从关系 $R$ 与 $S$ 的广义笛卡尔积中选取 $A$ 与 $B$ 相等的那些元组：
$$
R \underset{A=B}{\Join} S = \{ \overset{\frown}{t_rt_s} \mid t_r \in R \land t_s \in \land t_r[A] \theta t_s[B] \}
$$
<img src="..\..\..\pictures\equi_join_relationAlgbra.png"  style="width:59%;" align=center  />

###### （2）自然连接（[Natural join](https://www.w3resource.com/sql/joins/natural-join.php)）

​	自然连接是一种特殊的等值连接。它要求两个关系中进行比较的分量必须是同名的属性组，并且结果中合并重复的属性列。
$$
R\Join S = \{ \overset{\frown}{t_rt_s[U-B]} \mid t_r \in R \land t_s \in \land t_r[A] \theta t_s[B] \}
$$
其中，$U$ 为 $R$ 和 $S$ 两者属性集并集，$B$ 为 $R$ 和 $S$ 两者属性集交集。

> 一般的连接操作都是从行的角度进行运算，但自然连接还需要取消重复列，所以是同时从行和列的角度进行运算。

如果把悬浮元组也保存在结果中，而在其他属性上填空值（NULL），那么这种连接就叫做**外连接**（outer join），记作 $R  ⟗  S $；如果只保持左边关系 $R$ 中的悬浮元组就叫做**左外连接**（left outer join 或 left join），记作 $R⟕S$；如果只保持左边关系 $R$ 中的悬浮元组就叫做**左外连接**（left outer join 或 left join），记作 $R⟖S$。

> 两个关系两个关系做自然连接时，选择两个关系在公共属性上值相等的元组组成新的关系。此时，关系 $R$ 中某些元组有可能在 $S$ 中不存在，从而造成 $R$ 中某些元组操作时被舍弃，同样， $S$ 中某些元组操作时也被舍弃。这些被舍弃的元组称为**悬浮元组**（dangling tuple）。
>
> <img src="..\..\..\pictures\outer_join_relationAlgebra.png"  style="width:55%;" align=left  />
>
> <img src="..\..\..\pictures\outer_join_relationAlgebra2.png"  style="width:53%;" align=center  />

---

##### 4. 除运算（division）

设关系 $R$ 除以关系 $S$ 的结果为关系 $T$ ，则 $T$ 包含所有在 $R$ 但不在 $S$ 中的属性及其值，且 $T$ 的元组与 $S$ 的元组的所有组合属于关系 $R$ 中。

下面利用**象集**来定义除法：

> 对于给定关系 $R(X,Y)$ 和 $S(Y,Z)$ 其中 $X、Y、Z$ 为属性组。$R $ 中的 $Y$ 与 $S$ 中的 $Y$ 可以有不同的属性名，但是必须出自相同的域集（domain）。 

$R$ 与 $S$ 的除运算得到一个新的关系 $P(X)$，$P$ 是 $R$ 中满足下列条件的元组在 $X$ 属性列上的投影：元组在 $X$ 上的分量值 $x$ 的象集 $Y_x$ 包含 $S$ 在 $Y$ 上投影的集合，记作
$$
R÷S=\{ t_r[X] \mid t_r \in R \land \Pi_Y(S) \subseteq Y_x  \}
$$
其中 $Y_x$ 为 $x$ 在 $R$ 中的象集，$x=t_r[X]$。 

> 除操作是同时从行和列的角度进行运算

> <img src="..\..\..\pictures\division_relationAlgebra.png"  style="width:53%;" align=left  />
>
> <img src="..\..\..\pictures\division_relationAlgebra2.png"  style="width:50%;" align=left  />

### 3. 程序员补充在最后

- 本节介绍了8种关系代数运算，其中并、差、笛卡尔积、选择和投影这5中运算为基本的运算。其他三种运算，即交、连接和除均可以用这五种运算来表达。

  > 引进交、连接和除并不增加语言的能力，但可以简化表达

- 关系代数中，上述运算经过有限次后形成的表达式称为**关系代数表达式**。

  > RA 的表达能力是有限的，因为其运算符没有传递推导的能力。即我是你父亲，我父亲对你而言什么身份，并不能得到推导。

  > so，所以有了关系演算 :) 



