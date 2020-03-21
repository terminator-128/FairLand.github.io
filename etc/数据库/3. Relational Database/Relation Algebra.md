# 关系代数

关系代数是一种抽象的查询语言，他对关系的运算来表达查询。

> 任何一种预算都是将一定的运算符作用于一定的运算对象上，得到预期的运算结果。所以运算对象、运算符、运算结果是运算的三大要素。

关系代数的运算对象是关系，运算结果亦为关系。

> 欧式空间？（雾）——菜鸡作者hhh

关系代数用到的运算符包括两类：集合运算符和专门的关系运算符。

<table style="width:80%" align="center" >
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

